---
title: Visualização do desenvolvedor
description: Descreve os recursos da visualização pública de desenvolvedor do Microsoft Teams
keywords: recursos do desenvolvedor de visualização do teams
ms.openlocfilehash: a09e715e4e2d4aba72726cc96c4d248c550a3ab1
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672745"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Public Developer Preview para o Microsoft Teams

>[!NOTE]
>Os recursos incluídos na visualização podem não ser concluídos e podem sofrer alterações antes de ficarem disponíveis no lançamento público. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

Developer Preview é um programa público para desenvolvedores que oferece acesso antecipado a recursos não liberados no Microsoft Teams. Isso permite explorar e testar os recursos futuros para a possível inclusão no aplicativo Microsoft Teams. Também agradecemos [comentários](~/feedback.md) sobre qualquer recurso na visualização do desenvolvedor. A visualização do desenvolvedor é habilitada por cliente do Microsoft Teams, portanto, você não precisa se preocupar em afetar toda a organização.

## <a name="developer-preview-app-manifest"></a>Manifesto do desenvolvedor preview app

Muitos recursos habilitados na visualização do desenvolvedor precisarão de alterações no arquivo JSON do manifesto do aplicativo. Para fazer isso, você precisará usar o [esquema de manifesto da visualização do desenvolvedor](~/resources/schema/manifest-schema-dev-preview.md) se usar este esquema, não será possível usar o [app Studio](~/concepts/build-and-test/app-studio-overview.md) para fazer essas alterações, nem será possível usá-lo para carregar o aplicativo para teste. Para carregar seu aplicativo, você precisará clicar no `More apps` ícone da barra de aplicativos e selecionar o `Upload a custom app link`. Usando esse método, você só pode carregar uma versão zipada do seu pacote de aplicativos.

Você pode achar útil usar o app Studio para criar partes de visualização não desenvolvedor do pacote de aplicativos e, em seguida, exportar esse pacote e editá `manifest.json` -lo manualmente para adicionar os recursos de visualização do desenvolvedor que você deseja usar. Depois de adicionar os recursos de visualização do desenvolvedor `manifest.json` ao arquivo, você não poderá importar novamente o pacote para o app Studio.

## <a name="enable-developer-preview"></a>Habilitar visualização do desenvolvedor

A visualização do desenvolvedor é habilitada em uma base por cliente, mas a opção para ativar a visualização do desenvolvedor é controlada no nível da organização. Para habilitar a opção de ativar a visualização do desenvolvedor para um indivíduo, você deve garantir que ela tenha a capacidade de carregar aplicativos personalizados. Confira [Configurando o locatário](~/concepts/build-and-test/prepare-your-o365-tenant.md) para obter mais informações.

O uso de um aplicativo que contém recursos de visualização do desenvolvedor pode fazer com que os clientes que não habilitaram a visualização do desenvolvedor se comportam inesperadamente. Se você não vir uma entrada para a visualização do desenvolvedor, o motivo mais provável é que sua organização não esteja configurada para carregamento de aplicativos.

### <a name="on-a-desktop-or-web-client"></a>Em um cliente da Web ou da área de trabalho

Para habilitar o Public Developer preview em um cliente da Web ou desktop, você precisa fazer o seguinte:

1. Habilitar o carregamento de aplicativos no console de administração do locatário, conforme descrito [aqui](~/concepts/build-and-test/prepare-your-o365-tenant.md).
1. Clique em seu perfil (na parte superior direita ou inferior esquerda da interface do Teams) para exibir o menu Teams.
1. Selecione about → Developer Preview.
1. Selecione **alternar para a visualização do desenvolvedor**.

### <a name="on-a-mobile-client"></a>Em um cliente móvel

Para habilitar o Public Developer preview em um cliente móvel, você precisa fazer o seguinte:

1. Habilitar o carregamento de aplicativos no console de administração do locatário, conforme descrito [aqui](~/concepts/build-and-test/prepare-your-o365-tenant.md).
1. Abra o menu de alto-reinício na parte superior esquerda e selecione **configurações**.
1. Selecione **sobre**.
1. Clique em alternar visualização do desenvolvedor.

## <a name="disable-developer-preview"></a>Desabilitar a visualização do desenvolvedor

Use o mesmo item de menu em About → Developer Preview e clique nele para desativá-lo.

## <a name="features-available-in-developer-preview"></a>Recursos disponíveis na visualização do desenvolvedor

Para obter uma lista completa dos recursos atualmente habilitados na visualização do desenvolvedor, confira: [recursos na visualização do desenvolvedor público](../../resources/dev-preview/developer-preview-features.md).
