---
title: Carregar seu aplicativo personalizado
description: Saiba como realizar o sideload de seu aplicativo no Microsoft Teams. O sideload é comum ao testar e depurar um aplicativo durante o desenvolvimento.
ms.topic: how-to
author: surbhigupta
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: 96b80409697c9347fac82138d0e929c5c874725a
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558097"
---
# <a name="upload-your-app-in-teams"></a>Carregar seu aplicativo no Teams

Você pode realizar o sideload de aplicativos do Microsoft Teams sem precisar publicar em sua organização ou na loja do Teams. Isso faz sentido nos seguintes cenários:

* Você deseja testar e depurar um aplicativo localmente por conta própria ou com outros desenvolvedores.
* Você criou um aplicativo para você mesmo para automatizar um fluxo de trabalho.
* Você criou um aplicativo para um pequeno conjunto de usuários, como seu grupo de trabalho.

> [!NOTE]
> O sideload de seu aplicativo várias vezes exibe mais de uma instância para extensões de mensagens.

> [!IMPORTANT]
> Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e DoD (Departamento de Defesa).

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

   a. Selecione **Adicionar** para adicionar seu aplicativo pessoal.</br>b. Use o menu suspenso para adicionar seu aplicativo a uma Equipe ou chat.

    :::image type="content" source="~/assets/images/publish-app/teams-app-detail.png" alt-text="Descrição do aplicativo":::

## <a name="troubleshoot"></a>Solução de problemas

Se o aplicativo não conseguir realizar o sideload ou se houver problemas para carregar, verifique as seguintes opções:

1. Certifique-se de ter seguido todas as instruções para [criar seu pacote de aplicativos](../../concepts/build-and-test/apps-package.md).
1. [Validar seu pacote de aplicativos](https://dev.teams.microsoft.com/appvalidation.html).
1. Verifique se o manifesto do aplicativo corresponde ao [esquema](../../resources/schema/manifest-schema.md).

## <a name="manage-your-apps"></a>Gerenciar seus aplicativos

Gerenciar seus aplicativos permite que os usuários tenham um lugar dedicado para gerenciar, atualizar e remover seus aplicativos, permissões e assinaturas no cliente do Teams. Os usuários podem instalar seus aplicativos a partir de **Gerenciar seus aplicativos**.

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

1. Selecione **Exibir atualização**, uma janela com a opção de atualização será exibida.
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
> * Você não pode remover totalmente a atividade de bot pessoal. Se você remover o aplicativo e adicioná-lo novamente, a nova comunicação com o bot acrescentará à conversa anterior com ele.
> * No momento, você não pode migrar seu aplicativo personalizado para a loja do Teams. Se você quiser listar seu aplicativo na loja do Teams, confira [Publicar seu aplicativo na loja do Microsoft Teams](appsource/publish.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
>[Crie aplicativos para reuniões do Teams](../../apps-in-teams-meetings/teams-apps-in-meetings.md)

## <a name="see-also"></a>Confira também

* [Configurar opções de instalação padrão](~/concepts/deploy-and-publish/add-default-install-scope.md)
* [Mantenha seu aplicativo Microsoft Teams publicado](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)
