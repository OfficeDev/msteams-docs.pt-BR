---
title: Carregar seu aplicativo personalizado
description: Saiba como realizar o sideload de seu aplicativo no Microsoft Teams. O sideload é comum ao testar e depurar um aplicativo durante o desenvolvimento.
ms.topic: how-to
author: surbhigupta
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: a9ac73d3c3e41c5c57892273e788855a16642457
ms.sourcegitcommit: 3dc9b539c6f7fbfb844c47a78e3b4d2200dabdad
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64571101"
---
# <a name="upload-your-app-in-microsoft-teams"></a>Carregar seu aplicativo no Microsoft Teams

Você pode realizar o sideload de aplicativos do Microsoft Teams sem precisar publicar em sua organização ou na loja do Teams. Isso faz sentido nos seguintes cenários:

* Você deseja testar e depurar um aplicativo localmente por conta própria ou com outros desenvolvedores.
* Você criou um aplicativo para você mesmo para automatizar um fluxo de trabalho.
* Você criou um aplicativo para um pequeno conjunto de usuários, como seu grupo de trabalho.

> [!IMPORTANT]
> Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e DoD (Departamento de Defesa).

## <a name="prerequisites"></a>Pré-requisitos

* Crie seu [pacote de aplicativos](~/concepts/build-and-test/apps-package.md) e [valide-o](https://dev.teams.microsoft.com/appvalidation.html) para erros.
* [Habilitar o upload de aplicativos personalizados](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) no Teams.
* Verifique se o aplicativo está em execução e é acessível por meio de HTTPs.

## <a name="upload-your-app"></a>Carregar seu aplicativo

Você pode fazer o sideload do aplicativo para uma equipe, chat, reunião ou para uso pessoal, dependendo de como você configurou o escopo do aplicativo.

1. Acesse o cliente do Teams com sua [conta de desenvolvimento Microsoft 365](https://developer.microsoft.com/en-us/microsoft-365/dev-program).
1. Expanda **Aplicativos** e selecione **Gerenciar aplicativos**.
1. Selecione **Fazer o upload de um aplicativo personalizado**.
1. Selecione o arquivo .zip do pacote do aplicativo.
2. Adicione seu aplicativo ao Teams de acordo com suas necessidades:</br>

   a. Selecione **Adicionar** para adicionar seu aplicativo pessoal.</br>
   b. Use o menu suspenso para adicionar seu aplicativo a uma Equipe ou chat.

![Criar um aplicativo do Teams](~/assets/videos/app-teams.gif)

## <a name="troubleshooting"></a>Solução de problemas

Se o aplicativo não conseguir realizar o sideload ou se houver problemas para carregar, verifique as seguintes opções:

1. Verifique se você seguiu todas as instruções para [criar pacote do aplicativo](../../concepts/build-and-test/apps-package.md).
1. [Validar seu pacote de aplicativos](https://dev.teams.microsoft.com/appvalidation.html).
1. Verifique se o manifesto do aplicativo corresponde ao [esquema](../../resources/schema/manifest-schema.md).

## <a name="access-your-app"></a>Acessar seus aplicativos

O Teams fornece várias maneiras de abrir aplicativos. Para obter mais informações, consulte [acessar seus aplicativos no Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).

## <a name="update-your-app"></a>Atualize seu aplicativo

Você não precisará realizar o sideload do aplicativo novamente se fizer alterações de código (elas são refletidas no Teams em tempo real). No entanto, você deverá reinstalar se alterar as configurações do aplicativo.

## <a name="remove-your-app"></a>Remover seu aplicativo

Para remover seu aplicativo, clique com o botão direito do mouse no ícone do aplicativo no Teams e selecione **Desinstalar**.

> [!NOTE]
>
> * Você não pode remover totalmente a atividade de bot pessoal. Se você remover o aplicativo e adicioná-lo novamente, a nova comunicação com o bot acrescentará à conversa anterior com ele.
> * No momento, você não pode migrar seu aplicativo personalizado para a loja do Teams. Se você quiser listar seu aplicativo na loja do Teams, confira [Publicar seu aplicativo na loja do Microsoft Teams](appsource/publish.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Use seu aplicativo Teams](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b)

## <a name="see-also"></a>Confira também

* [Configurar opções de instalação padrão](~/concepts/deploy-and-publish/add-default-install-scope.md)
* [Mantenha seu aplicativo Microsoft Teams publicado](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)
