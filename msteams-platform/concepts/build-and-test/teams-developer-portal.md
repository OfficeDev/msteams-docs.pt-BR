---
title: Portal do Desenvolvedor do Teams
description: Neste artigo, saiba mais sobre o Portal do Desenvolvedor e como criar um aplicativo novo e importar um aplicativo existente no Portal do Desenvolvedor do Teams.
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: b0619fc328e6bc30decfe5868692281037489654
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615132"
---
# <a name="developer-portal-for-teams"></a>Portal do Desenvolvedor do Teams

O <a href="https://dev.teams.microsoft.com" target="_blank">Portal do Desenvolvedor para Teams</a> é a principal ferramenta para configurar, distribuir e gerenciar seus aplicativos do Microsoft Teams. Com o Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de runtime e muito mais.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="A captura de tela é um exemplo que mostra a home page do Portal do Desenvolvedor para Teams.":::

> [!NOTE]
>
> * Atualmente, o Portal do Desenvolvedor não está disponível para locatários do GCC (Government Community Cloud) –High ou do DoD (Departamento de Defesa).
> * No entanto, você pode usar um locatário regular para criar um aplicativo no Portal do Desenvolvedor, baixar o aplicativo e carregar o aplicativo usando [Microsoft Graph](/graph/api/teamsapp-publish?view=graph-rest-1.0&tabs=http&preserve-view=true) para uma nuvem nacional. Para obter mais informações, consulte [Implantações de nuvem nacional](/graph/deployments).

## <a name="register-an-app"></a>Registrar um aplicativo

O Portal do Desenvolvedor fornece as seguintes maneiras de registrar um aplicativo do Teams:

* Crie e registre um aplicativo novo.
* Importe um pacote de aplicativo existente.

### <a name="create-and-register-a-brand-new-app"></a>Criar e registrar um aplicativo novo

O portal do desenvolvedor permite que você crie um aplicativo novo:

1. Faça [logon no Portal do](https://dev.teams.microsoft.com) Desenvolvedor, **selecione Aplicativos** no painel esquerdo.

   :::image type="content" source="../../assets/images/tdp/home-page.png" alt-text="A captura de tela é um exemplo que mostra a home page do Portal do Desenvolvedor para Teams.":::

1. Selecione **Novo aplicativo e** insira o nome do aplicativo.

   :::image type="content" source="../../assets/images/tdp/enter-app-name-tdp.png" alt-text="A captura de tela mostra como criar um novo aplicativo no Portal do Desenvolvedor para Teams." lightbox="../../assets/images/tdp/create-new-app-in-tdp.png":::

1. Selecione **Adicionar**.

Agora você criou com êxito um novo aplicativo e pode ver todas as informações básicas do novo aplicativo.

:::image type="content" source="../../assets/images/tdp/basic-information-app-tdp.png" alt-text="A captura de tela é um exemplo que mostra as informações básicas do aplicativo que você criou no Portal do Desenvolvedor para Teams.":::

### <a name="import-an-existing-app"></a>Importar um aplicativo existente

Siga as etapas para importar e gerenciar seu aplicativo existente no Portal do Desenvolvedor.

1. No Portal do Desenvolvedor, selecione **Aplicativos** no painel esquerdo.
1. Selecione **Importar Aplicativo**.

   :::image type="content" source="../../assets/images/tdp/import-app.png" alt-text="A captura de tela mostra como importar seu aplicativo existente no Portal do Desenvolvedor do Teams para gerenciar seus aplicativos.":::

1. Selecione o arquivo de manifesto do aplicativo e, em seguida, **selecione Abrir**.
1. Selecione **Importar**.

> [!NOTE]
>
> * O Portal do Desenvolvedor cria uma ID de aplicativo exclusiva e bloqueia a ID do aplicativo teams registrado. Você não pode editar ou fornecer uma ID de sua escolha, o que impede que as IDs de aplicativo duplicadas para vários aplicativos.
> * Se você criar um aplicativo usando o Kit de Ferramentas do Microsoft Teams para Visual Studio Code, poderá gerenciar seu aplicativo no Portal do Desenvolvedor. Para obter mais informações, consulte [Criar aplicativos com o kit de ferramentas do Teams e o Visual Studio Code](~/toolkit/visual-studio-code-overview.md).
> * Você pode importar um aplicativo existente criado no App Studio para o Portal do Desenvolvedor.

## <a name="see-also"></a>Confira também

[Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
