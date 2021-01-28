---
title: Visualização do Desenvolvedor
description: Descreve os recursos na Visualização pública de desenvolvedor do Microsoft Teams
ms.topic: conceptual
keywords: recursos de desenvolvedor de visualização do Teams
ms.openlocfilehash: b8e8847d71ec3a571d434f952c79f3dd6a8f5bf1
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014072"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Visualização pública do desenvolvedor para o Microsoft Teams

>[!NOTE]
>Os recursos incluídos na visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis na versão pública. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

A Visualização do Desenvolvedor é um programa público para desenvolvedores que fornece acesso antecipado a recursos não lançados no Microsoft Teams. Isso permite que você explore e teste os recursos futuros para inclusão potencial em seu aplicativo do Microsoft Teams. Também damos as [boas-vindas aos comentários](~/feedback.md) sobre qualquer recurso na visualização do desenvolvedor. A visualização do desenvolvedor é habilitada por cliente do Microsoft Teams, portanto, você não precisa se preocupar em afetar toda a organização.

## <a name="developer-preview-app-manifest"></a>Manifesto do aplicativo de visualização do desenvolvedor

Muitos recursos habilitados na visualização do desenvolvedor exigirão alterações no arquivo JSON do manifesto do aplicativo. Para fazer isso, você precisará [](~/resources/schema/manifest-schema-dev-preview.md) usar o esquema de manifesto da visualização do desenvolvedor Se você usar esse esquema, não poderá usar o [App Studio](~/concepts/build-and-test/app-studio-overview.md) para fazer essas alterações, nem poderá usá-lo para carregar seu aplicativo para teste. Para carregar seu aplicativo, você precisará clicar no ícone na barra de `More apps` aplicativos e, em seguida, selecionar o `Upload a custom app link` . Usando esse método, você só pode carregar uma versão recortada do pacote do aplicativo.

Você pode achar útil usar o App Studio para criar as partes de visualização que não são do desenvolvedor do pacote do aplicativo e, em seguida, exportar esse pacote e editar manualmente o arquivo para adicionar os recursos de visualização do desenvolvedor que você deseja `manifest.json` usar. Depois de adicionar recursos de visualização do desenvolvedor ao arquivo, você não poderá importar novamente o `manifest.json` pacote para o App Studio.

## <a name="enable-developer-preview"></a>Habilitar a visualização do desenvolvedor

A visualização do desenvolvedor é habilitada por cliente, mas a opção para ativar a visualização do desenvolvedor é controlada no nível da organização. Para habilitar a opção de ativar a visualização do desenvolvedor para um indivíduo, você deve garantir que eles tenham a capacidade de carregar aplicativos personalizados. Consulte [como configurar seu locatário](~/concepts/build-and-test/prepare-your-o365-tenant.md) para obter informações adicionais.

Usar um aplicativo que contenha recursos de visualização do desenvolvedor pode fazer com que os clientes que não tenham habilitado a visualização do desenvolvedor se comportem inesperadamente. Se você não vir uma entrada para visualização do desenvolvedor, o motivo mais provável é que sua organização não está configurada para carregamento de aplicativos.

### <a name="on-a-desktop-or-web-client"></a>Em um cliente da Web ou da área de trabalho

Para habilitar a visualização do desenvolvedor público em uma área de trabalho ou cliente Web, você precisa fazer o seguinte:

1. Habilitando o carregamento de aplicativos no console de administração do seu locatário, conforme descrito [aqui.](~/concepts/build-and-test/prepare-your-o365-tenant.md)
1. Clique em seu perfil (no canto superior direito ou inferior esquerdo da interface do Teams) para exibir o menu do Teams.
1. Selecione Sobre a visualização → desenvolvedor.
1. Selecione **Alternar para Visualização do Desenvolvedor.**

### <a name="on-a-mobile-client"></a>Em um cliente móvel

Para habilitar a visualização do desenvolvedor público em um cliente móvel, você precisa fazer o seguinte:

1. Habilitando o carregamento de aplicativos no console de administração do seu locatário, conforme descrito [aqui.](~/concepts/build-and-test/prepare-your-o365-tenant.md)
1. Abra o menu hambúrguer no canto superior esquerdo e selecione **Configurações.**
1. Selecione **Sobre**.
1. Clique na alternância de visualização do desenvolvedor.

## <a name="disable-developer-preview"></a>Desabilitar a visualização do desenvolvedor

Use o mesmo item de menu em Sobre → Desenvolvedor e clique nele para desativar.

## <a name="features-available-in-developer-preview"></a>Recursos disponíveis na visualização do desenvolvedor

Para uma lista completa dos recursos habilitados no momento na visualização do desenvolvedor, consulte: [Recursos na visualização do desenvolvedor público.](../../resources/dev-preview/developer-preview-features.md)
