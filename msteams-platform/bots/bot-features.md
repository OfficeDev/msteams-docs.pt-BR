---
title: Bots e SDKs
author: surbhigupta
description: Visão geral das ferramentas e SDKs para criar Microsoft Teams bots.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 52f933aaddd5a02319ae1c0a35e9a4a26b617b57
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104319"
---
# <a name="bots-and-sdks"></a>Bots e SDKs

Você pode criar um bot que funciona Microsoft Teams com uma das seguintes ferramentas ou funcionalidades:

* [Microsoft Bot Framework SDK](#bots-with-the-microsoft-bot-framework)
* [Agentes virtuais do Power](#bots-with-power-virtual-agents)
* [Assistente Virtual](~/samples/virtual-assistant.md)
* [Webhooks e conectores](#bots-with-webhooks-and-connectors)

## <a name="bots-with-the-microsoft-bot-framework"></a>Bots com o Microsoft Bot Framework

Seu Teams bot consiste no seguinte:

* Um serviço Web publicamente acessível hospedado por você.
* Um registro do Bot Framework para seu serviço Web.
* Seu Teams do aplicativo, que conecta o cliente Teams ao serviço Web.

> [!TIP]
> Use o Portal do Desenvolvedor para registrar seu serviço Web com o Bot Framework e especificar as configurações do aplicativo. Para obter mais informações, consulte [gerenciar seus aplicativos com o Portal do Desenvolvedor para Teams](~/concepts/build-and-test/teams-developer-portal.md).

O [Bot Framework](https://dev.botframework.com/) é um SDK avançado usado para criar bots usando C#, Java, Python e JavaScript. Se você já tiver um bot baseado no Bot Framework, poderá modificá-lo facilmente para funcionar Teams. Use C# ou Node.js para aproveitar nossos [SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e métodos básicos do SDK do Bot Builder da seguinte maneira:

* Use tipos de cartão especializados, como o cartão Office 365 conector.
* Defina Teams de canal específicos em atividades.
* Processar solicitações de extensão de mensagem.

> [!IMPORTANT]
> Você pode desenvolver Teams aplicativos em qualquer tecnologia de programação da Web e chamar as [APIs REST do Bot Framework](/bot-framework/rest-api/bot-framework-rest-overview) diretamente. Mas você deve executar o tratamento de token em todos os casos.

## <a name="bots-with-power-virtual-agents"></a>Bots com Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) é um serviço de chatbot criado na plataforma Microsoft Power e no Bot Framework. O processo de desenvolvimento do Power Virtual Agent usa uma abordagem guiada, sem código e interface gráfica que capacita os membros da equipe a criar e manter facilmente um agente virtual inteligente. Depois de criar seu chatbot no [portal Power Virtual Agents,](https://powervirtualagents.microsoft.com) você pode [integrá-lo facilmente ao Teams](how-to/add-power-virtual-agents-bot-to-teams.md). Para obter mais informações sobre como começar, [consulte Power Virtual Agents documentação](/power-virtual-agents).

>[!NOTE]
>Você não deve usar o Microsoft Power Platform para criar aplicativos que devem ser publicados na Teams de aplicativos. Os aplicativos do Microsoft Power Platform podem ser publicados somente na loja de aplicativos de uma organização.

## <a name="bots-with-webhooks-and-connectors"></a>Bots com webhooks e conectores

Webhooks e conectores conectam seu bot aos seus serviços Web. Usando webhooks e conectores, você pode criar um bot para interação básica, como criar um fluxo de trabalho ou outros comandos simples. Eles estão disponíveis apenas na equipe em que você os cria e se destinam a processos simples específicos para o fluxo de trabalho da sua empresa. Para obter mais informações, confira [o que são webhooks e conectores](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="advantages-of-bots"></a>Vantagens dos bots

Os bots no Microsoft Teams podem fazer parte de uma conversa privadas, um chat em grupo ou um canal em uma equipe. Cada escopo fornece oportunidades e desafios exclusivos para seu bot de conversa.

| Em um canal | Em um chat em grupo | Em um chat um-para-um |
| :-- | :-- | :-- |
| Alcance maciço | Menos membros | Maneira tradicional |
| Interações individuais concisas | @mention ao bot  | Q&um bots |
| @mention ao bot | Semelhante ao canal | Bots que contam piadas e fazem anotações |

### <a name="in-a-channel"></a>Em um canal

Os canais contêm conversas encadeadas entre várias pessoas até dois mil. Isso potencialmente dá ao bot um grande alcance, mas as interações individuais devem ser concisas. As interações tradicionais de vários turnos não funcionam. Em vez disso, você deve procurar usar cartões interativos ou módulos de tarefa ou mover a conversa para uma conversa um-para-um para coletar muitas informações. Seu bot só tem acesso a mensagens onde ele está `@mentioned`. Você pode recuperar mensagens adicionais da conversa usando o Microsoft Graph permissões no nível da organização.

Os bots funcionam melhor em um canal nos seguintes casos:

* Notificações, em que você fornece um cartão interativo para que os usuários possam obter informações adicionais.
* Cenários de comentários, como pesquisas e pesquisas.
* Um único ciclo de solicitação ou resposta resolve interações e os resultados são úteis para vários membros da conversa.
* Bots sociais ou divertidos, onde você obtém uma imagem de gato incrível, escolhe aleatoriamente um vencedor e assim por diante.

### <a name="in-a-group-chat"></a>Em um chat em grupo

Os chats de grupo são conversas não-encadeadas entre três ou mais pessoas. Tendem a ter menos membros do que um canal e são mais temporários. Semelhante a um canal, o bot só tem acesso a mensagens em que ele está `@mentioned` diretamente.

Nos casos em que os bots funcionam melhor em um canal também funcionam melhor em um chat em grupo.

### <a name="in-a-one-to-one-chat"></a>Em um chat um-para-um

O chat um-para-um é uma maneira tradicional para um bot de conversa interagir com um usuário. Alguns exemplos de bots de conversa um-para-um são:

* Q&um bots
* bots que iniciam fluxos de trabalho em outros sistemas
* bots que contam piadas
* bots que anotam Antes de criar chatbots um-para-um, considere se uma interface baseada em conversa é a melhor maneira de apresentar sua funcionalidade.

## <a name="disadvantages-of-bots"></a>Desvantagens dos bots

Uma ampla caixa de diálogo entre o bot e o usuário é uma maneira lenta e complexa de concluir uma tarefa. Um bot que dá suporte a comandos excessivos, especialmente uma ampla variedade de comandos, não é bem-sucedido ou exibido positivamente pelos usuários.

### <a name="have-multi-turn-experiences-in-chat"></a>Ter experiências de vários turnos no chat

Uma caixa de diálogo extensiva exige que o desenvolvedor mantenha o estado. Para sair desse estado, um usuário deve ter um tempo limite ou selecionar **Cancelar**. Além disso, o processo é entediante. Por exemplo, consulte o seguinte cenário de conversa:

Agende uma reunião com Megan.

BOT: Encontrei 200 resultados, inclua um nome e sobrenome.

Agende uma reunião com Megan Bowen.

OK, que horas você gostaria de se encontrar com Megan Bowen?

USER: 13:00 pm.

Em qual dia?

### <a name="support-too-many-commands"></a>Suporte a muitos comandos

Como há apenas seis comandos visíveis no menu do bot atual, é improvável que algo mais seja usado com qualquer frequência. Bots que se aprofundam em uma área específica, em vez de tentarem ser um amplo assistente de trabalho e tarifa melhor.

### <a name="maintain-a-large-knowledge-base"></a>Manter uma grande base de dados de conhecimento

Uma das desvantagens dos bots é que é difícil manter uma grande recuperação base de dados de conhecimento respostas não listadas. Os bots são mais adequados para interações curtas e rápidas e não para verificar listas longas em busca de uma resposta.

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

O código a seguir fornece um exemplo de atividade de bot para um chat um-para-um:

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
| Bot de conversas do Teams | Sistema de mensagens e manipulação de eventos de conversa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot)|
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
