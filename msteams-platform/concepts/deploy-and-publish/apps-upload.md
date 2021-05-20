---
title: Upload seu aplicativo personalizado
description: Aprenda a carregar seu aplicativo de lado em Microsoft Teams. O sideloading é comum ao testar e depurar um aplicativo durante o desenvolvimento.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.openlocfilehash: 39e94317ceb615ecd7d5481276ffafed5afe5cde
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565190"
---
# <a name="upload-your-app-in-microsoft-teams"></a>Upload seu aplicativo em Microsoft Teams

Você pode carregar Microsoft Teams aplicativos sem ter que publicar na sua organização ou na loja Teams. Isso faz sentido nos seguintes cenários:

* Você quer testar e depurar um aplicativo localmente você mesmo ou com outros desenvolvedores.
* Você construiu um aplicativo só para você. Por exemplo, para automatizar um fluxo de trabalho.
* Você construiu um aplicativo para um pequeno conjunto de usuários, como, como, seu grupo de trabalho.

## <a name="prerequisites"></a>Pré-requisitos

* Crie seu [pacote de aplicativos](~/concepts/build-and-test/apps-package.md) e [valide-o](https://dev.teams.microsoft.com/appvalidation.html) para erros.
* [Habilite o upload personalizado de aplicativos](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) em Teams.
* Certifique-se de que seu aplicativo está em execução e acessível via HTTPs.

## <a name="upload-your-app"></a>Carregar seu aplicativo

Você pode carregar seu aplicativo de lado para uma equipe, bate-papo, reunião ou para uso pessoal, dependendo de como você configurou o escopo do seu aplicativo.

1. Faça login no Teams cliente com sua [conta de desenvolvimento Microsoft 365](~/build-your-first-app/build-and-run.md#prerequisites).
1. Selecione **Aplicativos** e escolha **Upload um aplicativo personalizado**.
1. Selecione seu pacote de aplicativo .zip arquivo. Uma instalação de monitores de diálogo.
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Captura de tela mostrando um exemplo de Teams aplicativo instalar a caixa de diálogo.":::
1. Adicione seu aplicativo a Teams.

## <a name="troubleshoot-upload-issues"></a>Solução de problemas de carregamento

Se o aplicativo não conseguir fazer a carga lateral, faça o seguinte até que o problema seja resolvido:

1. Volte as instruções para [criar seu pacote de aplicativos](../../concepts/build-and-test/apps-package.md).
1. [Valide seu pacote de aplicativos](https://dev.teams.microsoft.com/appvalidation.html) novamente.
1. Certifique-se de que o manifesto do aplicativo corresponda ao [esquema](../../resources/schema/manifest-schema.md)mais recente .

## <a name="access-your-app"></a>Acesse seu aplicativo

Teams fornece várias maneiras de abrir aplicativos. Para obter mais informações, consulte [acessar seus aplicativos em Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).

## <a name="update-your-app"></a>Atualize seu aplicativo

Você não precisa carregar seu aplicativo novamente se fizer alterações de código (estas são refletidas em Teams em tempo real). No entanto, você deve reinstalar se alterar qualquer configuração do aplicativo.

## <a name="remove-your-app"></a>Remova seu aplicativo

Para remover seu aplicativo, clique com o botão direito do mouse no ícone do aplicativo em Teams e selecione **Desinstalar**.

> [!NOTE]
> Você não pode remover totalmente a atividade do bot pessoal. Se você remover o aplicativo e adicioná-lo novamente, uma nova comunicação com o bot anexa à conversa anterior com ele.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Use seu aplicativo de Teams](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
