---
title: Bots e SDKs
author: surbhigupta
description: Neste artigo, aprenda ferramentas e SDKs para Microsoft Teams bots e bots com o Microsoft Bot Framework.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 0b344b6a2db0abc4d1769c47aca6f496f69b98d7
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142462"
---
# <a name="bots-and-sdks"></a>Bots e SDKs

Você pode criar um bot que funcione no Microsoft Teams com uma das seguintes ferramentas ou funcionalidades:

* [SDK do Microsoft Bot Framework](#bots-with-the-microsoft-bot-framework)
* [Agentes virtuais do Power](#bots-with-power-virtual-agents)
* [Assistente Virtual](~/samples/virtual-assistant.md)
* [Webhooks e conectores](#bots-with-webhooks-and-connectors)
* [Serviço de bot do Azure](#azure-bot-service)

## <a name="bots-with-the-microsoft-bot-framework"></a>Bots com o Microsoft Bot Framework

O bot do Teams consiste no seguinte:

* Um serviço Web publicamente acessível hospedado por você.
* Um Bot Framework para seu serviço Web.
* Seu pacote de aplicativos do Teams, que conecta o cliente do Teams ao seu serviço Web.

> [!TIP]
> Use o Portal do Desenvolvedor para registrar seu serviço Web com o Bot Framework e especificar as configurações do aplicativo. Para obter mais informações, confira [gerenciar seus aplicativos com o Portal do Desenvolvedor para o Teams](~/concepts/build-and-test/teams-developer-portal.md).

O [Bot Framework](https://dev.botframework.com/) é um SDK avançado usado para criar bots usando C#, Java, Python e JavaScript. Se você já tiver um bot baseado no Bot Framework, poderá modificá-lo facilmente para funcionar no Teams. Use C# ou Node.js para aproveitar nossos [SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e os métodos básicos SDK do Construtor de Bot da seguinte maneira:

* Use tipos de cartão especializados, como o cartão do Conector do Office 365.
* Defina dados de canal específicos do Teams em atividades.
* Processar solicitações de extensão de mensagem.

> [!IMPORTANT]
> Você pode desenvolver aplicativos do Teams em qualquer tecnologia de programação da Web e chamar as [APIs REST do Bot Framework](/bot-framework/rest-api/bot-framework-rest-overview) diretamente. Mas você deve executar o tratamento de token em todos os casos.

## <a name="bots-with-power-virtual-agents"></a>Bots com Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) é um serviço de chatbot criado na plataforma Microsoft Power e Bot Framework. O processo de desenvolvimento do Power Virtual Agent usa uma abordagem guiada, sem código e interface gráfica que capacita os membros da equipe a criar e manter facilmente um agente virtual inteligente. Depois de criar seu chatbot no portal [Power Virtual Agents](https://powervirtualagents.microsoft.com), você pode [integrá-lo facilmente ao Teams](how-to/add-power-virtual-agents-bot-to-teams.md). Para obter mais informações sobre como começar, consulte [a documentação Power Virtual Agents](/power-virtual-agents).

>[!NOTE]
>Você não deve usar o Microsoft Power Platform para criar aplicativos que devem ser publicados na loja de aplicativos do Teams. Os aplicativos do Microsoft Power Platform podem ser publicados somente na loja de aplicativos de uma organização.

## <a name="bots-with-webhooks-and-connectors"></a>Bots com webhooks e conectores

Webhooks e conectores conectam seu bot aos seus serviços Web. Usando webhooks e conectores, você pode criar um bot para interação básica, como criar um fluxo de trabalho ou outros comandos simples. Eles estão disponíveis apenas na equipe em que você os cria e são destinados a processos simples específicos para o fluxo de trabalho da sua empresa. Para obter mais informações, confira [o que são webhooks e conectores](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="azure-bot-service"></a>Serviço de bot do Azure

O serviço de bot do Azure, juntamente com o Bot Framework, fornece ferramentas para criar, testar, implantar e gerenciar bots inteligentes, tudo em um só lugar. Você também pode criar seu bot no serviço de bot do Azure.

> [!IMPORTANT]
> Os aplicativos de bot no Microsoft Teams estão disponíveis no GCC-High através do [Serviço de bot do Azure](/azure/bot-service/channel-connect-teams).

> [!NOTE]
> * Os bots no GCCH dão suporte apenas à versão de manifesto v1.10.
> * Não há suporte para URLs de imagem em Cartões Adaptáveis no ambiente GCCH. Você pode substituir uma URL de imagem pelo DataUri codificado em Base64.
> * O registro de canal de bot no Azure Governamental provisionará o bot do aplicativo Web, o serviço de aplicativo (plano do serviço de aplicativo) e o Application Insights também, mas não dá suporte para provisionar apenas o serviço de bot do Azure (sem serviço de aplicativo).
>   <details>
>   <summary><b>Se você quiser apenas fazer o registro de bot</b></summary>
>
>   * Vá para o grupo de recursos e exclua manualmente os recursos não utilizados. Como o serviço de aplicativo, o plano do serviço de aplicativo (se você criou durante o registro do bot) e o application insights (se você optar por habilita-lo durante o registro do bot).
>   * Você também pode usar az-cli para fazer o registro de bot:
>
>     1. Entre no Azure e defina a assinatura <br> 
>           &nbsp; az cloud set –name "AzureUSGovernment" <br> 
>           &nbsp; az account set –name "`subscriptionname/id`".<br>
>     1. Criar registro de aplicativo  
>           &nbsp; az ad app create --display-name "`name`" <br> 
>           &nbsp; --password "`password`" --available-to-other-tenants.<br> 
>           A ID do aplicativo seria criada aqui.<br>
>     1. Criar recurso de bot <br>
>           &nbsp; az bot create –resource-group "`resource-group`"<br>
>           &nbsp; --appid "`appid`"<br>
>           &nbsp; --name "`botid`"<br>
>           &nbsp; --tipo "registro".<br>
>
> </details>

Para o ambiente GCCH, você precisa registrar um bot [usando Azure Governamental portal](https://portal.azure.us).

:::image type="content" source="../assets/videos/abs-bot.gif" alt-text="Azure Governamental portal":::
<br>
<br>
As seguintes alterações são necessárias no bot para GCC-High ambiente:
<br>
<br>
<details>
<summary><b>Alterações de configuração</b></summary>

À medida que o registro do bot ocorre Azure Governamental portal, atualize as configurações do bot para se conectar às instâncias do Govermnet do Azure. Veja a seguir os detalhes de configuração:

| Nome da configuração | Valor |
|----|----|
| ChannelService | `https://botframework.azure.us` |
| OAuthUrl | `https://tokengcch.botframework.azure.us` |
| ToChannelFromBotLoginUrl | `https://login.microsoftonline.us/MicrosoftServices.onmicrosoft.us` |
| ToChannelFromBotoAuthScope | `https://api.botframework.us` |
| ToBotFromChannelTokenIssuer | `https://api.botframework.us`  |
| BotOpenIdMetadata | `https://login.botframework.azure.us/v1/.well-known/openidconfiguration` |

</details>
<br>
<details>
<summary><b>Atualizar para appsettings.json & startup.cs</b></summary>

1. **Atualizar appsettings.json:**

    * Defina `ConnectionName` como o nome da configuração de conexão OAuth que você adicionou ao seu bot.

    * Defina `MicrosoftAppId` e `MicrosoftAppPassword` como a ID do aplicativo e o segredo do aplicativo do seu bot.
    
    Dependendo dos caracteres do segredo do seu bot, talvez seja necessário que o XML escape da senha. Por exemplo, qualquer e comercial (&) precisa ser codificado como `&amp;`.

    ```json
    {
      "MicrosoftAppType": "",
      "MicrosoftAppId": "",
      "MicrosoftAppPassword": "",
      "MicrosoftAppTenantId": "",
      "ConnectionName": ""
    }
    ```
2. **Atualizar Startup.cs:**

    Para usar o OAuth em nuvens não públicas do *Azure*, como a nuvem governamental ou em bots com residência de dados, você deve adicionar o código a seguir no arquivo **Startup.cs** .
    
    ```csharp
    string uri = "<uri-to-use>";
    MicrosoftAppCredentials.TrustServiceUrl(uri);
    OAuthClientConfig.OAuthEndpoint = uri;
    ```
    
    Onde \<uri-to-use\> está um dos seguintes URIs:

    |**URI**|**Descrição**|
    |---|---|
    |`https://europe.api.botframework.com`|Para bots de nuvem pública com residência de dados na Europa.|
    |`https://unitedstates.api.botframework.com`|Para bots de nuvem pública com residência de dados no Estados Unidos.|
    |`https://apiGCCH.botframework.azure.us`|Para Estados Unidos bots de nuvem governamental sem residência de dados.|
    |`https://api.botframework.com`|Para bots de nuvem pública sem residência de dados. Esse é o URI padrão e não requer uma alteração em **Startup.cs**.|

3. A URL de redirecionamento para o registro de aplicativo do Azure deve ser atualizada para `https://tokengcch.botframework.azure.us/.auth/web/redirect`.

</details>

## <a name="advantages-of-bots"></a>Vantagens dos bots

Os bots no Microsoft Teams podem fazer parte de uma conversa privadas, um chat em grupo ou um canal em uma equipe. Cada escopo fornece oportunidades únicas e desafios para seu bot conversacional.

| Em um canal. | Em um chat em grupo | Chat Privado |
| :-- | :-- | :-- |
| Alcance enorme | Menos membros | Maneira tradicional |
| Interações individuais concisas | Bot de @menção  | Bots de P e R |
| Bot de @menção | Semelhante ao canal | Bots que contam piadas e fazem anotações |

### <a name="in-a-channel"></a>Em um canal.

Os canais contêm conversas encadeadas entre várias pessoas até dois mil. Isso potencialmente dá ao seu bot um alcance enorme, mas as interações individuais devem ser concisas. As interações tradicionais de vários turnos não funcionam. Em vez disso, procure usar cartões interativos ou módulos de tarefas, ou mover a conversa para uma conversa privada se precisar coletar muitas informações. Seu bot só tem acesso a mensagens em que está `@mentioned`. Você pode recuperar mensagens adicionais da conversa usando as permissões do Microsoft Graph no nível da organização.

Os bots funcionam melhor em um canal nos seguintes casos:

* Notificações, em que você fornece um cartão interativo para os usuários obterem informações adicionais.
* Comentários cenários como votações e pesquisas.
* Um único ciclo de solicitação ou resposta resolve interações e os resultados são úteis para vários membros da conversa.
* Bots sociais ou divertidos, em que você obtém uma imagem de gato incrível, escolhe aleatoriamente um vencedor e assim por diante.

### <a name="in-a-group-chat"></a>Em um chat em grupo

Os chats de grupo são conversas não-encadeadas entre três ou mais pessoas. Tendem a ter menos membros do que um canal e são mais temporários. Semelhante a um canal, seu bot só tem acesso a mensagens em que ele está `@mentioned` diretamente.

Nos casos em que os bots funcionam melhor em um canal também funcionam melhor em um chat em grupo.

### <a name="in-a-one-to-one-chat"></a>Chat Privado

O chat privado é a maneira tradicional de um bot de conversação interagir com um usuário. Alguns exemplos de bots de chat ptivado são:

* Bots de P e R
* bots que iniciam fluxos de trabalho em outros sistemas
* bots que contam piadas
* bots que usam anotações antes de criar chatbots privados, considere se uma interface baseada em conversa é a melhor maneira de apresentar sua funcionalidade.

## <a name="disadvantages-of-bots"></a>Desvantagens dos bots

Uma caixa de diálogo extensa entre o bot e o usuário é uma maneira lenta e complexa de concluir uma tarefa. Um bot que dá suporte a comandos excessivos, especialmente uma ampla variedade de comandos, não é bem-sucedido ou exibido positivamente pelos usuários.

### <a name="have-multi-turn-experiences-in-chat"></a>Ter experiências de vários turnos no chat

Uma caixa de diálogo extensa exige que o desenvolvedor mantenha o estado. Para sair desse estado, um usuário deve ter um tempo limite ou selecionar **Cancelar**. Além disso, o processo é entediante. Por exemplo, consulte o seguinte cenário de conversa:

USER: Agende uma reunião com Sara.

BOT: encontrei 200 resultados, inclua um nome e um sobrenome.

USER: Agende uma reunião com Sara Melo.

BOT: OK, a que hora você gostaria de se encontrar com Sara Melo?

USUÁRIO: 13h.

BOT: Em qual dia?

### <a name="support-too-many-commands"></a>Suporte a muitos comandos

Como há apenas seis comandos visíveis no menu do bot atual, é improvável que algo mais seja usado com qualquer frequência. Bots que se aprofundam em uma área específica em vez de tentar ser um amplo trabalho de assistente funcionam melhor.

### <a name="maintain-a-large-knowledge-base"></a>Manter uma grande base de dados de conhecimento

Uma das desvantagens dos bots é que é difícil manter uma grande recuperação base de dados de conhecimento respostas não listadas. Os bots são mais adequados para interações rápidas e curtas e não passam por listas longas em busca de uma resposta.

## <a name="code-snippets"></a>Trechos de código

O código a seguir fornece um exemplo de atividade de bot para um escopo de equipe de canal:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var mention = new Mention
    {
        Mentioned = turnContext.Activity.From,
        Text = $"<at>{XmlConvert.EncodeName(turnContext.Activity.From.Name)}</at>",
    };

    var replyActivity = MessageFactory.Text($"Hello {mention.Text}.");
    replyActivity.Entities = new List<Entity> { mention };

    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}

```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

this.onMessage(async (turnContext, next) => {
    const mention = {
        mentioned: turnContext.activity.from,
        text: `<at>${ new TextEncoder().encode(turnContext.activity.from.name) }</at>`,
    } as Mention;

    const replyActivity = MessageFactory.text(`Hello ${mention.text}`);
    replyActivity.entities = [mention];

    await turnContext.sendActivity(replyActivity);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});

```

---

O código a seguir fornece um exemplo de atividade de bot para um chat privado:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

// Handle message activity
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    turnContext.Activity.RemoveRecipientMention();
    var text = turnContext.Activity.Text.Trim().ToLower();
  await turnContext.SendActivityAsync(MessageFactory.Text($"Your message is {text}."), cancellationToken);
}
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript
this.onMessage(async (context, next) => {
    await context.sendActivity(MessageFactory.text("Your message is:" + context.activity.text));
    await next();
});
```

---

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NETCore | Node.js | Python|
|----------------|-----------------|--------------|----------------|-------|
| Bot de conversas do Teams | Sistema de mensagens e manipulação de eventos de conversa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|[Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot)|
| Exemplos de bot | Conjunto de exemplos de bot | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore) |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Manipuladores de atividade de bot](~/bots/bot-basics.md)

## <a name="see-also"></a>Confira também

* [Bots de chamadas e reuniões](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)
* [Conversas de bot](~/bots/how-to/conversations/conversation-basics.md)
* [Menus de comando do bot](~/bots/how-to/create-a-bot-commands-menu.md)
* [Fluxo de autenticação para bots no Microsoft Teams](~/bots/how-to/authentication/auth-flow-bot.md)
* [Usar módulos de tarefas dos bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
