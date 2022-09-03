---
title: Receber todas as mensagens do canal com RSC
author: surbhigupta12
description: Permitir que os bots recebam todas as mensagens de canal sem @mentioned permissões RSC. Leia na seção webApplicationInfo ou autorização no manifesto.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: db51bcddaa22a115330129ddc677f0401c8bd523
ms.sourcegitcommit: 82c585d287d61924ce3a3bba3e9caeff35c9a27a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586907"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Receber todas as mensagens do canal com RSC

O modelo de permissões de consentimento específico de recursos (RSC), originalmente desenvolvido para APIs de Teams Graph, é estendido a cenários de bot.

Usando o RSC, você pode agora solicitar aos proprietários da equipe o consentimento de um bot para receber mensagens de usuários através dos canais padrão em uma equipe sem ser @mencionado. Esta funcionalidade é habilitada especificando a `ChannelMessage.Read.Group` permissão no manifesto de um aplicativo Teams habilitado com RCS. Após a configuração, os proprietários da equipe podem conceder consentimento durante o processo de instalação do aplicativo.

Para obter mais informações sobre como habilitar o RSC para seu aplicativo, consulte [consentimento específico do recurso em Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).

## <a name="enable-bots-to-receive-all-channel-messages"></a>Habilitar bots para receber todas as mensagens de canal

A `ChannelMessage.Read.Group` permissão RSC é estendida para bots. Com o consentimento do usuário, essa permissão permite que os aplicativos de grafo obtenham todas as mensagens em uma conversa e os bots recebam todas as mensagens de canal sem serem @mentioned.

> [!NOTE]
>
> * Os serviços que precisam de acesso a todos os dados de mensagens do Teams devem usar as APIs Graph que também fornecem acesso a dados arquivados em canais e chats.
> * Os bots devem usar `ChannelMessage.Read.Group` a permissão RSC adequadamente para criar e aprimorar a experiência envolvente para os usuários na equipe ou eles não passarão na aprovação da loja. A descrição do aplicativo deve incluir como o bot usa os dados lidos.
> * A `ChannelMessage.Read.Group` permissão RSC pode não ser usada por bots como uma maneira de extrair grandes quantidades de dados do cliente.

## <a name="update-app-manifest"></a>Atualizar manifesto do aplicativo

Para que seu bot receba todas as mensagens de canal, o RSC deve ser configurado no manifesto do aplicativo Teams com a `ChannelMessage.Read.Group`permissão especificada na `webApplicationInfo` propriedade.

:::image type="content" source="~/bots/how-to/conversations/Media/appmanifest.png" alt-text="Captura de tela da atualização do manifesto do aplicativo.":::

A seguir, um exemplo do objeto de `webApplicationInfo`:

* **id**: Seu ID de aplicativo do Microsoft Azure Active Directory (Azure AD). Esta pode ser a mesma que a ID do seu bot.
* **recurso**: Qualquer cadeia de caracteres. Este campo não tem nenhuma operação no RSC, mas deve ser adicionado e ter um valor para evitar resposta de erro.
* **applicationPermissions**: As permissões de RSC para seu aplicativo com `ChannelMessage.Read.Group` devem ser especificadas. Para obter mais informações, consulte [permissões específicas do recurso](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).

O código a seguir fornece um exemplo do CSS:

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
1. Selecione as reticências &#x25CF;&#x25CF;&#x25CF; no painel esquerdo. O menu suspenso de pesquisa.
1. Selecione **Gerenciar equipe** a partir do menu suspenso. Os detalhes aparecem.

   :::image type="content" source="Media/managingteam.png" alt-text="Captura de tela da opção Gerenciar equipe no aplicativo Teams.":::

1. Selecione **Aplicativos**. Múltiplos aplicativos aparecem.

1. Escolha **Upload um aplicativo personalizado** no canto inferior direito.

      :::image type="content" source="Media/uploadingcustomapp.png" alt-text="Captura de tela da opção carregar um aplicativo personalizado.":::
  
1. Selecione o pacote do aplicativo a partir da caixa de diálogo **Abrir**.

1. Selecione **Abrir**.

      :::image type="content" source="Media/selectapppackage.png" alt-text="Captura de tela da caixa de diálogo abrir para selecionar o pacote do aplicativo." lightbox="Media/selectapppackage.png":::

1. Selecione **Adicionar** através do pop-up com detalhes do aplicativo para adicionar o bot à sua equipe selecionada.

      :::image type="content" source="Media/addingbot.png" alt-text="Captura de tela do botão Adicionar para adicionar um bot a uma equipe." lightbox="Media/addingbot.png":::

1. Selecione um canal e insira uma mensagem no canal para seu bot.

    O bot recebe a mensagem sem ser @mencionado.

      :::image type="content" source="Media/botreceivingmessage.png" alt-text="Captura de tela de um bot recebendo mensagem em um canal." lightbox="Media/botreceivingmessage.png":::

## <a name="code-snippets"></a>Trechos de código

O código a seguir fornece um exemplo de permissões RSC:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

// Handle when a message is addressed to the bot. 
// When rsc is enabled the method will be called even when bot is addressed without being @mentioned
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text("Using RSC the bot can receive messages across channels in team without being @mentioned."));
}
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

// Handle when a message is addressed to the bot. 
// When rsc is enabled the method will be called even when bot is addressed without being @mentioned
this.onMessage(async (context, next) => {
   await context.sendActivity(MessageFactory.text("Using RSC the bot can receive messages across channles in team without being @mentioned."))
   await next();
});
```

---

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|Mensagens de canal com permissões RSC| Aplicativo de amostra do Microsoft Teams demonstrando como um bot pode receber todas as mensagens de canal com RSC sem ser @mencionado.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/nodejs) |

## <a name="see-also"></a>Confira também

* [Conversas de bot](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Consentimento específico do recurso](/microsoftteams/resource-specific-consent)
* [Testar o consentimento específico do recurso](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Fazer o upload de aplicativos personalizados no Teams](~/concepts/deploy-and-publish/apps-upload.md)
* [Listar respostas a mensagens em um canal](/graph/api/chatmessage-list-replies?view=graph-rest-1.0&tabs=http&preserve-view=true)
