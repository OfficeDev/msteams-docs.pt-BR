---
title: Carregar seu aplicativo personalizado
description: Saiba como realizar o sideload de seu aplicativo no Microsoft Teams. O sideload é comum ao testar e depurar um aplicativo durante o desenvolvimento.
ms.topic: how-to
author: surbhigupta
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: ffa7cdb0fabf07254c90590fe94fe2347c35658c
ms.sourcegitcommit: 377a4b712b50a211851aeecc1029414939945390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68044676"
---
# <a name="upload-your-app-in-teams"></a>Carregar seu aplicativo no Teams

Você pode realizar o sideload de aplicativos do Microsoft Teams sem precisar publicar em sua organização ou na loja do Teams. Isso faz sentido nos seguintes cenários:

* Você deseja testar e depurar um aplicativo localmente por conta própria ou com outros desenvolvedores.
* Você criou um aplicativo para você mesmo para automatizar um fluxo de trabalho.
* Você criou um aplicativo para um pequeno conjunto de usuários, como seu grupo de trabalho.

> [!NOTE]
> O sideload do aplicativo de extensão de mensagens várias vezes exibe mais de uma instância para extensões de mensagens.

> [!IMPORTANT]
>
> * Atualmente, o sideload de aplicativos só é possível na GCC (Nuvem da Comunidade Governamental) e não é possível no GCC-High e departamento de defesa (DOD).
> * A instalação do aplicativo tem suporte apenas no aplicativo da área de trabalho do Teams.

## <a name="prerequisites"></a>Pré-requisitos

* Crie seu [pacote de aplicativos](~/concepts/build-and-test/apps-package.md) e [valide-o](https://dev.teams.microsoft.com/appvalidation.html) para erros.
* [Habilitar o upload de aplicativos personalizados](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) no Teams.
* Verifique se o aplicativo está em execução e é acessível por meio de HTTPs.

## <a name="upload-your-app"></a>Carregar seu aplicativo

Você pode fazer o sideload do aplicativo para uma equipe, chat, reunião ou para uso pessoal, dependendo de como você configurou o escopo do aplicativo.

1. Acesse o cliente do Teams com sua [conta de desenvolvimento Microsoft 365](https://developer.microsoft.com/en-us/microsoft-365/dev-program).
1. Selecione **Aplicativos** > **Gerenciar seus aplicativos** e **Publicar um aplicativo**.

    :::image type="content" source="~/assets/images/publish-app/manage-apps.png" alt-text="Publicar um aplicativo":::

1. Selecione **Fazer o upload de um aplicativo personalizado**.

   :::image type="content" source="~/assets/images/publish-app/publish-app.png" alt-text="Carregar um aplicativo personalizado":::.

1. Selecione o arquivo .zip do pacote do aplicativo.
1. Adicione seu aplicativo ao Teams de acordo com suas necessidades:</br>

   a. Select **Add** to add your personal app.</br>
   b. Use the dropdown menu to add your app to a Team or chat.

    :::image type="content" source="~/assets/images/publish-app/teams-app-detail.png" alt-text="Descrição do aplicativo":::

## <a name="troubleshoot"></a>Solução de problemas

Se o aplicativo não realizar o sideload ou encontrar problemas para carregar, verifique as seguintes opções:

1. Certifique-se de ter seguido todas as instruções para [criar seu pacote de aplicativos](../../concepts/build-and-test/apps-package.md).
1. [Validar seu pacote de aplicativos](https://dev.teams.microsoft.com/appvalidation.html).
1. Verifique se o manifesto do aplicativo corresponde ao esquema [mais recente](../../resources/schema/manifest-schema.md).

## <a name="manage-your-apps"></a>Gerenciar seus aplicativos

Manage your apps allows users to have a dedicated place to manage, update and remove their apps, permissions, and subscriptions on the Teams client. The users can install the apps from **Manage your apps**.

### <a name="access-your-app"></a>Acessar seus aplicativos

Para acessar aplicativos por meio de **Gerenciar seus aplicativos**, siga as etapas:

1. Acesse **Aplicativos** e selecione **Gerenciar seus aplicativos** no Teams para exibir os aplicativos instalados em todos os seus canais ou para uso pessoal em um formato de lista.

    :::image type="content" source="~/assets/images/publish-app/manage-apps-list.png" alt-text="lista dos aplicativos Acessar equipes":::

1. Selecione a lista suspensa do aplicativo para exibir todos os escopos em que o aplicativo está instalado.

    :::image type="content" source="~/assets/images/publish-app/app-scopes.png" alt-text="Escopo do aplicativo Acessar equipes":::

1. Selecione o escopo do aplicativo para ir para o aplicativo no canal ou no modo de exibição pessoal. A lista de escopos consiste apenas em escopo pessoal e escopo de equipes. Os aplicativos instalados no escopo do chat em grupo não são exibidos nessa exibição no momento.

O Teams fornece várias maneiras de abrir aplicativos. Para obter mais informações, consulte [acessar seus aplicativos no Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).

### <a name="update-your-app"></a>Atualize seu aplicativo

Você não precisará realizar o sideload do aplicativo novamente se fizer alterações de código (elas são refletidas no Teams em tempo real). No entanto, você deverá reinstalar se alterar as configurações do aplicativo.

Se uma atualização estiver disponível para seu aplicativo, a opção **Atualização disponível** está habilitada. Para atualizar, siga as etapas:

1. Selecione **Atualização disponível** para exibir a atualização.

     :::image type="content" source="~/assets/images/publish-app/update-available.png" alt-text="Atualizar o aplicativo do Teams.":::

1. Selecione **Exibir atualização**. Uma janela com a opção de atualização é exibida.
1. Selecione o botão **Atualizar** para atualizar seu aplicativo.

     :::image type="content" source="~/assets/images/publish-app/update-window.png" alt-text="Atualizar o aplicativo do Teams em gerenciar aplicativos.":::

     :::image type="content" source="~/assets/images/publish-app/updated-app.png" alt-text="Aplicativo atualizado":::

### <a name="remove-your-app"></a>Remover seu aplicativo

Para remover o aplicativo do Teams, siga as etapas:

1. Localize o aplicativo em **Gerenciar seu aplicativo**.

1. Selecione &nbsp;:::image type="content" source="~/assets/images/publish-app/bin-icon.png" alt-text="Remover aplicativo no Teams.":::&nbsp; no escopo do aplicativo instalado.

    :::image type="content" source="~/assets/images/publish-app/uninstall-from-channel.png" alt-text="Remover o aplicativo em um canal.":::

1. Selecione **Remover** para remover seu aplicativo.

    :::image type="content" source="~/assets/images/publish-app/remove-app-teams.png" alt-text="Remover um aplicativo do Teams.":::

> [!NOTE]
>
> * You can't remove personal bot activity entirely. If you remove the app and add it again, new communication with the bot appends to the previous conversation with it.
> * No momento, você não pode migrar seu aplicativo personalizado para a loja do Teams. Se você quiser listar seu aplicativo na loja do Teams, confira [Publicar seu aplicativo na loja do Microsoft Teams](appsource/publish.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
>[Crie aplicativos para reuniões do Teams](../../apps-in-teams-meetings/teams-apps-in-meetings.md)

## <a name="see-also"></a>Confira também

* [Configurar opções de instalação padrão](~/concepts/deploy-and-publish/add-default-install-scope.md)
* [Mantenha seu aplicativo Microsoft Teams publicado](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)
* [Adicionar o aplicativo ao chat](/graph/api/chat-post-installedapps)
