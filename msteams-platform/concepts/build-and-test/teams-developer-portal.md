---
title: Portal do Desenvolvedor do Teams
description: Neste artigo, saiba mais sobre o Portal do Desenvolvedor e como criar um novo aplicativo e importar um aplicativo existente no Portal do Desenvolvedor do Teams.
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 3c6444f041a996b908e2c6444fecf7e3dc68ee40
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791801"
---
# <a name="developer-portal-for-teams"></a>Portal do Desenvolvedor do Teams

O <a href="https://dev.teams.microsoft.com" target="_blank">Portal do Desenvolvedor para Teams</a> é a principal ferramenta para configurar, distribuir e gerenciar seus aplicativos do Microsoft Teams. Com o Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de runtime e muito mais.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="A captura de tela é um exemplo que mostra a página inicial do Portal do Desenvolvedor para Teams.":::

> [!NOTE]
>
> * Atualmente, o Portal do Desenvolvedor não está disponível para locatários do GCC (Government Community Cloud)-High ou do DoD (Departamento de Defesa).
> * No entanto, você pode usar um locatário regular para criar um aplicativo no Portal do Desenvolvedor, baixar o aplicativo e carregar o aplicativo usando [Microsoft Graph](/graph/api/teamsapp-publish?view=graph-rest-1.0&tabs=http&preserve-view=true) para uma nuvem nacional. Para obter mais informações, consulte [Implantações de nuvem nacional](/graph/deployments).

## <a name="register-an-app"></a>Registrar um aplicativo

O Portal do Desenvolvedor fornece as seguintes maneiras de registrar um aplicativo do Teams:

* [Crie e registre um novo aplicativo](#create-and-register-a-brand-new-app).
* [Importar um pacote de aplicativo existente](#import-an-existing-app).

### <a name="create-and-register-a-brand-new-app"></a>Criar e registrar um novo aplicativo

O portal do Desenvolvedor permite que você crie um novo aplicativo:

1. Faça logon no [Portal do Desenvolvedor](https://dev.teams.microsoft.com), selecione **Aplicativos** no painel esquerdo.

   :::image type="content" source="../../assets/images/tdp/home-page.png" alt-text="A captura de tela é um exemplo que mostra a página inicial do Portal do Desenvolvedor para Teams.":::

1. Selecione **Novo aplicativo** e insira o nome do aplicativo.

   :::image type="content" source="../../assets/images/tdp/enter-app-name-tdp.png" alt-text="A captura de tela mostra como criar um novo aplicativo no Portal de Desenvolvedores do Teams." lightbox="../../assets/images/tdp/create-new-app-in-tdp.png":::

1. Selecione **Adicionar**.

Agora você criou com êxito um novo aplicativo e pode ver todas as informações básicas do novo aplicativo.

:::image type="content" source="../../assets/images/tdp/basic-information-app-tdp.png" alt-text="A captura de tela é um exemplo que mostra as informações básicas do aplicativo que você criou no Portal de Desenvolvedores do Teams.":::

### <a name="import-an-existing-app"></a>Importar um aplicativo existente

Siga as etapas para importar e gerenciar seu aplicativo existente no Portal do Desenvolvedor.

1. No Portal do Desenvolvedor, selecione **Aplicativos** no painel esquerdo.
1. Selecione **Importar Aplicativo**.

   :::image type="content" source="../../assets/images/tdp/import-app.png" alt-text="A captura de tela mostra como importar seu aplicativo existente no Portal do Desenvolvedor para o Teams para gerenciar seus aplicativos.":::

1. Selecione o arquivo de manifesto do aplicativo e selecione **Abrir**.
1. Selecione **Importar**.

> [!NOTE]
>
> * O Portal do Desenvolvedor cria uma ID de aplicativo exclusiva e bloqueia a ID do aplicativo do Teams registrado. Você não pode editar ou fornecer uma ID de sua escolha, o que impede ter IDs de aplicativo duplicadas para vários aplicativos.
> * Se você criar um aplicativo usando o Kit de Ferramentas do Microsoft Teams para Visual Studio Code, poderá gerenciar seu aplicativo no Portal do Desenvolvedor. Para obter mais informações, confira [Criar aplicativos com kit de ferramentas do teams e código do Visual Studio](~/toolkit/visual-studio-code-overview.md).
> * Você pode importar um aplicativo existente que você criou no App Studio para o Portal do Desenvolvedor.

## <a name="see-also"></a>Confira também

[Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
