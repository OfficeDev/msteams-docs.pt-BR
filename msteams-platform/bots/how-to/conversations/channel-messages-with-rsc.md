---
title: Receber todas as mensagens do canal com RSC
author: surbhigupta12
description: Receber todas as mensagens de canal com permissões RSC
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: abe6bc821c9e4ffe05b1cf35480f9c559401014e
ms.sourcegitcommit: 55d4b4b721a33bacfe503bc646b412f0e3b0203e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2022
ms.locfileid: "62185439"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Receber todas as mensagens do canal com RSC

O modelo de permissões de consentimento específico do recurso (RSC), originalmente desenvolvido para APIs Teams Graph, é estendido para cenários de bot.

Usando o RSC, agora você pode solicitar que os proprietários da equipe consentam para que um bot receba mensagens de usuário nos canais padrão em uma equipe sem @mentioned. Essa funcionalidade é habilitada especificando a permissão no manifesto de um `ChannelMessage.Read.Group` aplicativo Teams RSC habilitado. Após a configuração, os proprietários da equipe podem conceder consentimento durante o processo de instalação do aplicativo.

Para obter mais informações sobre a habilitação do RSC para seu aplicativo, consulte [resource-specific consent in Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).

## <a name="enable-bots-to-receive-all-channel-messages"></a>Habilitar bots para receber todas as mensagens de canal

A `ChannelMessage.Read.Group` permissão RSC é estendida para bots. Com o consentimento do usuário, essa permissão permite que os aplicativos gráficos recebam todas as mensagens em uma conversa e bots recebam todas as mensagens de canal sem serem @mentioned.

> [!NOTE]
> * Os serviços que precisam de acesso a todos os Teams de mensagens devem usar as APIs Graph que também fornecem acesso a dados arquivados em canais e chats.
> * Os bots devem usar a permissão RSC adequadamente para criar e aprimorar a experiência envolvente para os usuários na equipe ou eles não passarão na aprovação `ChannelMessage.Read.Group` do armazenamento. A descrição do aplicativo deve incluir como o bot usa os dados lidos.
> * A permissão RSC pode não ser usada por bots como uma maneira de extrair `ChannelMessage.Read.Group` grandes quantidades de dados do cliente. 

## <a name="update-app-manifest"></a>Atualizar manifesto do aplicativo

Para que o bot receba todas as mensagens de canal, o RSC deve ser configurado no manifesto do aplicativo Teams com a permissão `ChannelMessage.Read.Group` especificada na `webApplicationInfo` propriedade.
![Atualizar manifesto do aplicativo](~/bots/how-to/conversations/Media/appmanifest.png)

Veja a seguir um exemplo do `webApplicationInfo` objeto:

* **id**: Sua Azure Active Directory (AAD) ID do aplicativo. Isso pode ser o mesmo que sua ID de bot.
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

## <a name="sideload-in-a-team"></a>Sideload em uma equipe

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

## <a name="code-snippets"></a>Trechos de código

O código a seguir fornece um exemplo de permissões RSC:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

// Handle when a message is addressed to the bot. 
// When rsc is enabled the method will be called even when bot is addressed without being @mentioned
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
        await turnContext.SendActivityAsync(MessageFactory.Text("Using RSC the bot can recieve messages across channles in team without being @mentioned."));
}
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

// Handle when a message is addressed to the bot. 
// When rsc is enabled the method will be called even when bot is addressed without being @mentioned
this.onMessage(async (context, next) => {
   await context.sendActivity(MessageFactory.text("Using RSC the bot can recieve messages across channles in team without being @mentioned."))
   await next();
});
```

---

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|Mensagens de canal com permissões RSC| Microsoft Teams exemplo de aplicativo demonstrando como um bot pode receber todas as mensagens de canal com RSC sem @mentioned.|  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/csharp) |    [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/nodejs) |

## <a name="see-also"></a>Confira também

* [Conversas de bot](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Consentimento específico do recurso](/microsoftteams/resource-specific-consent)
* [Testar o consentimento específico do recurso](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Upload aplicativo personalizado no Teams](~/concepts/deploy-and-publish/apps-upload.md)
