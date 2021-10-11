---
title: Visualização do desenvolvedor
description: Descreve os recursos na Visualização pública do desenvolvedor Microsoft Teams
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Recursos de desenvolvedor de visualização do teams
ms.openlocfilehash: 8cf3f4faf4387aba6ea6238b0469bae840aba87f
ms.sourcegitcommit: c04a1a792773a9d5c61169c5702d94a8c478ad1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2021
ms.locfileid: "60260615"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Visualização do desenvolvedor público para Microsoft Teams

>[!NOTE]
>Os recursos incluídos na visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis na versão pública. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

O Developer Preview é um programa público para desenvolvedores que fornece acesso antecipado a recursos não lançados no Microsoft Teams. Isso permite que você explore e teste os recursos futuros para inclusão potencial em seu Microsoft Teams app. Também damos [boas-vindas aos comentários](~/feedback.md) sobre qualquer recurso na visualização do desenvolvedor. A visualização do desenvolvedor está habilitada por cliente Microsoft Teams, portanto, você não precisa se preocupar em afetar toda a sua organização.

## <a name="developer-preview-app-manifest"></a>Manifesto do aplicativo de visualização do desenvolvedor

Muitos recursos habilitados na visualização do desenvolvedor exigirão alterações no arquivo JSON do manifesto do aplicativo. Para fazer isso, você precisará usar o esquema de manifesto de [visualização do desenvolvedor.](~/resources/schema/manifest-schema-dev-preview.md) Se você usar esse esquema, não poderá usar o [App Studio](~/concepts/build-and-test/app-studio-overview.md) para fazer essas alterações, nem poderá usá-lo para carregar seu aplicativo para teste. Para carregar seu aplicativo, você precisará clicar no ícone na barra de aplicativos `More apps` e, em seguida, selecione `Upload a custom app link` o . Usando esse método, você só pode carregar uma versão de zipped do pacote do aplicativo.

Você pode achar útil usar o App Studio para criar as partes de visualização que não são do desenvolvedor do pacote de aplicativos e, em seguida, exportar esse pacote e editar manualmente o arquivo para adicionar os recursos de visualização do desenvolvedor que você deseja `manifest.json` usar. Depois de adicionar recursos de visualização do desenvolvedor ao arquivo, você não poderá importar novamente o `manifest.json` pacote para o App Studio.

## <a name="enable-developer-preview"></a>Habilitar a visualização do desenvolvedor

A visualização do desenvolvedor é habilitada por cliente, mas a opção de ativar a visualização do desenvolvedor é controlada no nível da organização. Para habilitar a opção de ativar a visualização do desenvolvedor para um indivíduo, você deve garantir que eles tenham a capacidade de carregar aplicativos personalizados. Consulte [configurando seu locatário](~/concepts/build-and-test/prepare-your-o365-tenant.md) para obter informações adicionais.

O uso de um aplicativo que contém recursos de visualização do desenvolvedor pode fazer com que os clientes que não tenham habilitado a visualização do desenvolvedor se comportem inesperadamente. Se você não vir uma entrada para visualização do desenvolvedor, o motivo mais provável é que sua organização não está configurada para carregamento de aplicativos.

### <a name="on-a-desktop-or-web-client"></a>Em uma área de trabalho ou cliente Web

Para habilitar a visualização do desenvolvedor público em uma área de trabalho ou cliente Web, você precisa fazer o seguinte:

1. Habilitando o carregamento de aplicativos no console de administração do locatário, conforme descrito [aqui](~/concepts/build-and-test/prepare-your-o365-tenant.md).
1. Clique em seu perfil (no canto superior direito ou inferior esquerdo da interface Teams) para exibir o menu Teams.
1. Selecione Sobre → visualização do desenvolvedor.
1. Selecione **Alternar para Visualização do Desenvolvedor.**

### <a name="on-a-mobile-client"></a>Em um cliente móvel

Para habilitar a visualização do desenvolvedor público em um cliente móvel, você precisa fazer o seguinte:

1. Habilitando o carregamento de aplicativos no console de administração do locatário, conforme descrito [aqui](~/concepts/build-and-test/prepare-your-o365-tenant.md).
1. Abra o menu hambúrguer na parte superior esquerda e selecione **Configurações**.
1. Selecione **Sobre**.
1. Clique na alternância visualização do desenvolvedor.

## <a name="disable-developer-preview"></a>Desabilitar a visualização do desenvolvedor

Use o mesmo item de menu em Sobre → visualização do desenvolvedor e clique nele para a desativar.



