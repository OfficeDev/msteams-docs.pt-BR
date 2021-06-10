---
title: Receber todas as mensagens do canal com RSC
author: surbhigupta12
description: Receber todas as mensagens de canal com permissões RSC
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 833bdbc015cf852fcd899ce4e75f742448b89978
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631239"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Receber todas as mensagens do canal com RSC

> [!NOTE]
> Esse recurso está disponível apenas na [visualização de desenvolvedor](../../../resources/dev-preview/developer-preview-intro.md) público.

O modelo de permissões de consentimento específico do recurso (RSC), originalmente desenvolvido para APIs Teams Graph, agora é estendido para cenários de bot.

Atualmente, os bots só podem receber mensagens de canal do usuário quando estão @mentioned. Usando o RSC, agora você pode solicitar que os proprietários da equipe consentam para que um bot receba mensagens de usuário nos canais padrão em uma equipe sem @mentioned. Essa funcionalidade é habilitada especificando a permissão no manifesto de um `ChannelMessage.Read.Group` aplicativo Teams RSC habilitado. Após a configuração, os proprietários da equipe podem conceder consentimento durante o processo de instalação do aplicativo.

Para obter mais informações sobre a habilitação do RSC para seu aplicativo, consulte [resource-specific consent in Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).

## <a name="enable-bots-to-receive-all-channel-messages"></a>Habilitar bots para receber todas as mensagens de canal

A `ChannelMessage.Read.Group` permissão RSC é estendida para bots. Com o consentimento do usuário, essa permissão permite que os aplicativos gráficos recebam todas as mensagens em uma conversa e bots recebam todas as mensagens de canal sem serem @mentioned.

## <a name="update-app-manifest"></a>Atualizar manifesto do aplicativo

Para que o bot receba todas as mensagens de canal, o RSC deve ser configurado no manifesto do aplicativo Teams com a permissão `ChannelMessage.Read.Group` especificada na `webApplicationInfo` propriedade.

![Atualizar manifesto do aplicativo](~/bots/how-to/conversations/Media/appmanifest.png)

Veja a seguir um exemplo do `webApplicationInfo` objeto:

* **id**: Sua Azure Active Directory (AAD) iD do aplicativo. Isso pode ser o mesmo que sua ID de bot.
* **resource**: Qualquer cadeia de caracteres. Este campo não tem nenhuma operação no RSC, mas deve ser adicionado e ter um valor para evitar a resposta de erro.
* **applicationPermissions**: as permissões RSC para seu aplicativo com `ChannelMessage.Read.Group` devem ser especificadas. Para obter mais informações, consulte [permissões específicas do recurso](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).

O código a seguir fornece um exemplo do manifesto do aplicativo:

```json
"webApplicationInfo": {
"id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
"resource": "https://AnyString",
"applicationPermissions": [
"ChannelMessage.Read.Group"
    ]
  }
```

## <a name="sideload-in-a-team-to-test"></a>Fazer sideload em uma equipe para testar

Para fazer sideload em uma equipe para testar, se todas as mensagens de canal em uma equipe com RSC são recebidas sem @mentioned:

1. Selecione ou crie uma equipe.
1. Selecione as releições &#x25CF;&#x25CF;&#x25CF; no painel esquerdo. O menu suspenso é exibido.
1. Selecione **Gerenciar equipe** no menu suspenso. Os detalhes aparecem.

   ![Gerenciando aplicativos em equipe](~/bots/how-to/conversations/Media/managingteam.png)

1. Selecione **Aplicativos**. Vários aplicativos aparecem.
1. Selecione **Upload um aplicativo personalizado** no canto inferior direito.

    ![Carregando aplicativo personalizado](~/bots/how-to/conversations/Media/uploadingcustomapp.png)

1. Selecione o pacote do aplicativo na **caixa de diálogo** Abrir.
1. Selecione **Abrir**.

    ![Selecionar pacote de aplicativos](~/bots/how-to/conversations/Media/selectapppackage.png)

1. Selecione **Adicionar** no pop-up de detalhes do aplicativo, para adicionar o bot à sua equipe selecionada.

    ![Adicionando o bot](~/bots/how-to/conversations/Media/addingbot.png)

1. Selecione um canal e insira uma mensagem no canal do bot.

    O bot recebe a mensagem sem ser @mentioned.

    ![Bot recebe mensagem](~/bots/how-to/conversations/Media/botreceivingmessage.png)

## <a name="see-also"></a>Confira também

* [Conversas de bot](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Consentimento específico do recurso](/microsoftteams/resource-specific-consent)
* [Testar o consentimento específico do recurso](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Upload aplicativo personalizado no Teams](~/concepts/deploy-and-publish/apps-upload.md)
