---
title: Upload seu aplicativo personalizado
description: Saiba como fazer sideload do aplicativo Microsoft Teams. O sideload é comum ao testar e depurar um aplicativo durante o desenvolvimento.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.openlocfilehash: 93df0d92ce6912888dd1932be3295ca92fa5a967
ms.sourcegitcommit: 2c4c77dc8344f2fab8ed7a3f7155f15f0dd6a5ce
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58345259"
---
# <a name="upload-your-app-in-microsoft-teams"></a>Upload seu aplicativo no Microsoft Teams

Você pode fazer sideload Microsoft Teams aplicativos sem precisar publicar na sua organização ou no Teams store. Isso faz sentido nos seguintes cenários:

* Você deseja testar e depurar um aplicativo localmente ou com outros desenvolvedores.
* Você criou um aplicativo apenas para si mesmo. Por exemplo, para automatizar um fluxo de trabalho.
* Você criou um aplicativo para um pequeno conjunto de usuários, como seu grupo de trabalho.

> [!IMPORTANT]
> Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e Departamento de Defesa (DOD).

## <a name="prerequisites"></a>Pré-requisitos

* Crie seu [pacote de aplicativos](~/concepts/build-and-test/apps-package.md) [e valide-o](https://dev.teams.microsoft.com/appvalidation.html) para erros.
* [Habilitar o carregamento personalizado de aplicativos](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) Teams.
* Certifique-se de que seu aplicativo está em execução e acessível por meio de HTTPs.

## <a name="upload-your-app"></a>Carregar seu aplicativo

Você pode fazer sideload do aplicativo em uma equipe, chat, reunião ou para uso pessoal, dependendo de como você configurou o escopo do aplicativo.

1. Faça logoff no cliente Teams com sua [conta Microsoft 365 de desenvolvimento.](~/build-your-first-app/build-and-run.md#prerequisites)
1. Selecione **Aplicativos** e escolha **Upload um aplicativo personalizado.**
1. Selecione o arquivo .zip pacote do aplicativo. Uma caixa de diálogo de instalação é exibida.
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Captura de tela mostrando um exemplo de uma caixa de diálogo Teams instalação do aplicativo.":::
1. Adicione seu aplicativo ao Teams.

## <a name="troubleshoot-upload-issues"></a>Solução de problemas de carregamento

Se o aplicativo não fizer sideload, faça o seguinte até que o problema seja resolvido:

1. Volte pelas instruções para criar [seu pacote de aplicativos.](../../concepts/build-and-test/apps-package.md)
1. [Valide seu pacote de aplicativo novamente.](https://dev.teams.microsoft.com/appvalidation.html)
1. Verifique se o manifesto do aplicativo corresponde ao [esquema mais recente.](../../resources/schema/manifest-schema.md)

## <a name="access-your-app"></a>Acessar seu aplicativo

Teams fornece várias maneiras de abrir aplicativos. Para obter mais informações, [consulte access your apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).

## <a name="update-your-app"></a>Atualizar seu aplicativo

Você não precisa fazer sideload do aplicativo novamente se fizer alterações de código (elas são refletidas em Teams em tempo real). No entanto, você deve reinstalar se alterar qualquer configuração de aplicativo.

## <a name="remove-your-app"></a>Remover seu aplicativo

Para remover seu aplicativo, clique com o botão direito do mouse no ícone do aplicativo no Teams e selecione **Desinstalar**.

> [!NOTE]
> Não é possível remover totalmente a atividade de bot pessoal. Se você remover o aplicativo e adicioná-lo novamente, a nova comunicação com o bot acrescenta à conversa anterior com ele.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Usar seu Teams aplicativo](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
