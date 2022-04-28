---
title: Receber todas as mensagens do canal com RSC
author: surbhigupta12
description: Receber todas as mensagens de canal com permissões RSC
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: a78910b083943e5296f3e0d50eae00a713f194aa
ms.sourcegitcommit: e40383d9081bf117030f7e6270140e6b94214e8b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65102056"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Receber todas as mensagens do canal com RSC

O modelo de permissões de RSC (consentimento específico do recurso), originalmente desenvolvido para APIs de Teams Graph, é estendido para cenários de bot.

Usando a RSC, agora você pode solicitar que os proprietários da equipe consentam para que um bot receba mensagens do usuário entre canais padrão em uma equipe sem ser @mentioned. Essa funcionalidade é habilitada especificando `ChannelMessage.Read.Group` a permissão no manifesto de um aplicativo Teams RSC habilitado. Após a configuração, os proprietários da equipe podem conceder consentimento durante o processo de instalação do aplicativo.

Para obter mais informações sobre como habilitar o RSC para seu aplicativo, consulte [o consentimento específico do recurso em Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).

## <a name="enable-bots-to-receive-all-channel-messages"></a>Habilitar bots para receber todas as mensagens de canal

A `ChannelMessage.Read.Group` permissão RSC é estendida para bots. Com o consentimento do usuário, essa permissão permite que os aplicativos de grafo obtenham todas as mensagens em uma conversa e os bots recebam todas as mensagens de canal sem serem @mentioned.

> [!NOTE]
>
> * Os serviços que precisam de acesso a todos os Teams de mensagens devem usar as APIs de Graph que também fornecem acesso a dados arquivados em canais e chats.
> * Os bots devem usar `ChannelMessage.Read.Group` a permissão RSC adequadamente para criar e aprimorar a experiência envolvente para os usuários na equipe ou eles não passarão na aprovação da loja. A descrição do aplicativo deve incluir como o bot usa os dados lidos.
> * A `ChannelMessage.Read.Group` permissão RSC pode não ser usada por bots como uma maneira de extrair grandes quantidades de dados do cliente.

## <a name="update-app-manifest"></a>Atualizar manifesto do aplicativo

Para que o bot receba todas as mensagens de canal, o RSC `ChannelMessage.Read.Group` deve ser configurado no manifesto Teams aplicativo com a permissão especificada na `webApplicationInfo` propriedade.

![Atualizar manifesto do aplicativo](~/bots/how-to/conversations/Media/appmanifest.png)


A seguir está um exemplo do `webApplicationInfo` objeto:

* **id**: sua Microsoft Azure Active Directory (Azure AD) ID do aplicativo. Isso pode ser o mesmo que a ID do bot.
* **resource**: qualquer cadeia de caracteres. Esse campo não tem nenhuma operação na RSC, mas deve ser adicionado e ter um valor para evitar a resposta de erro.
* **applicationPermissions**: as permissões de RSC para seu aplicativo com `ChannelMessage.Read.Group` devem ser especificadas. Para obter mais informações, consulte [permissões específicas do recurso](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).

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

Para realizar o sideload em uma equipe para testar se todas as mensagens de canal em uma equipe com RSC são recebidas sem serem @mentioned:

1. Selecione ou crie uma equipe.
1. Selecione as reticências &#x25CF;&#x25CF;&#x25CF; no painel esquerdo. O menu suspenso é exibido.
1. Selecione **Gerenciar equipe** no menu suspenso. Os detalhes são exibidos.

   ![Gerenciando aplicativos na equipe](~/bots/how-to/conversations/Media/managingteam.png)

      :::image type="content" source="Media/managingteam.png" alt-text="gerenciando a equipe"border="true":::

1. Selecione **Aplicativos**. Vários aplicativos são exibidos.
1. Selecione **Upload um aplicativo personalizado** no canto inferior direito.

      :::image type="content" source="Media/uploadingcustomapp.png" alt-text="carregando aplicativo personalizado":::
  
1. Selecione o pacote do aplicativo na **caixa de diálogo** Abrir.
1. Selecione **Abrir**.

      :::image type="content" source="Media/selectapppackage.png" alt-text="Selecione o pacote do aplicativo"lightbox="Media/selectapppackage.png"border="true":::

1. Selecione **Adicionar** no pop-up de detalhes do aplicativo para adicionar o bot à equipe selecionada.

      :::image type="content" source="Media/addingbot.png" alt-text="Adicionando bot"lightbox="Media/addingbot.png"border="true":::

1. Selecione um canal e insira uma mensagem no canal para o bot.

    O bot recebe a mensagem sem ser @mentioned.

      :::image type="content" source="Media/botreceivingmessage.png" alt-text="Mensagem de recebimento de bot"lightbox="Media/botreceivingmessage.png"border="true":::

## <a name="code-snippets"></a>Trechos de código

O código a seguir fornece um exemplo de permissões RSC:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

// Handle when a message is addressed to the bot. 
// When rsc is enabled the method will be called even when bot is addressed without being @mentioned
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text("Using RSC the bot can recieve messages across channels in team without being @mentioned."));
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
|Mensagens de canal com permissões RSC| Microsoft Teams aplicativo de exemplo demonstrando como um bot pode receber todas as mensagens de canal com RSC sem ser @mentioned.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/nodejs) |

## <a name="see-also"></a>Confira também

* [Conversas de bot](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Consentimento específico do recurso](/microsoftteams/resource-specific-consent)
* [Testar o consentimento específico do recurso](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Upload aplicativo personalizado no Teams](~/concepts/deploy-and-publish/apps-upload.md)
