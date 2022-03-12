---
title: Bots e SDKs
author: surbhigupta
description: Visão geral das ferramentas e SDKs para criar Microsoft Teams bots.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 5a95159df887033bca339efd871261938aecb07d
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453884"
---
# <a name="bots-and-sdks"></a>Bots e SDKs

Você pode criar um bot que funcione Microsoft Teams com uma das seguintes ferramentas ou recursos:

* [Microsoft Bot Framework SDK](#bots-with-the-microsoft-bot-framework)
* [Agentes virtuais do Power](#bots-with-power-virtual-agents)
* [Assistente Virtual](~/samples/virtual-assistant.md)
* [Webhooks e conectores](#bots-with-webhooks-and-connectors)

## <a name="bots-with-the-microsoft-bot-framework"></a>Bots com a Microsoft Bot Framework

Seu Teams bot consiste no seguinte:

* Um serviço Web publicamente acessível hospedado por você.
* Um registro da Estrutura de Bots para seu serviço Web.
* Seu Teams aplicativo, que conecta o cliente Teams ao seu serviço Web.

> [!TIP]
> Use o Portal do Desenvolvedor para registrar seu serviço Web com a Estrutura de Bots e especificar as configurações do aplicativo. Para obter mais informações, [consulte manage your apps with the Developer Portal for Teams](~/concepts/build-and-test/teams-developer-portal.md).

A [Estrutura de Bot](https://dev.botframework.com/) é um SDK rico usado para criar bots usando C#, Java, Python e JavaScript. Se você já tiver um bot baseado na Estrutura de Bot, poderá modificá-lo facilmente para funcionar Teams. Use o C# ou Node.js tirar proveito de nossos [SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e métodos básicos do SDK do Construtor de Bots da seguinte forma:

* Use tipos de cartão especializados como o cartão Office 365 conector.
* De Teams dados de canal específicos em atividades.
* Processar solicitações de extensão de mensagens.

> [!IMPORTANT]
> Você pode desenvolver Teams aplicativos em qualquer tecnologia de programação da Web e chamar as [APIs REST da](/bot-framework/rest-api/bot-framework-rest-overview) Estrutura de Bot diretamente. Mas você deve executar o tratamento de token em todos os casos.

## <a name="bots-with-power-virtual-agents"></a>Bots com Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) é um serviço de chatbot criado na plataforma do Microsoft Power e no Bot Framework. O processo de desenvolvimento do Power Virtual Agent usa uma abordagem guiada, sem código e interface gráfica que permite aos membros da equipe criar e manter facilmente um agente virtual inteligente. Depois de criar seu chatbot no [portal Power Virtual Agents,](https://powervirtualagents.microsoft.com) você pode [integrá-lo facilmente com Teams](how-to/add-power-virtual-agents-bot-to-teams.md). Para obter mais informações sobre como começar, [consulte Power Virtual Agents documentação](/power-virtual-agents).

>[!NOTE]
>Você não deve usar o Microsoft Power Platform para criar aplicativos que devem ser publicados no Teams de aplicativos. Os aplicativos da Plataforma Microsoft Power só podem ser publicados no armazenamento de aplicativos de uma organização.

## <a name="bots-with-webhooks-and-connectors"></a>Bots com webhooks e conectores

Webhooks e conectores conectam seu bot aos seus serviços Web. Usando webhooks e conectores, você pode criar um bot simples para interação básica, como a criação de um fluxo de trabalho ou outros comandos simples. Eles estão disponíveis apenas na equipe em que você os cria e se destinam a processos simples específicos do fluxo de trabalho da sua empresa. Para obter mais informações, consulte [o que são webhooks e conectores](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="advantages-of-bots"></a>Vantagens dos bots

Os bots no Microsoft Teams podem fazer parte de uma conversa privadas, um chat em grupo ou um canal em uma equipe. Cada escopo fornece oportunidades e desafios exclusivos para seu bot de conversa.

| Em um canal | Em um chat em grupo | Em um chat um para um |
| :-- | :-- | :-- |
| Alcance massivo | Menos membros | Maneira tradicional |
| Concisa interações individuais | @mention para bot  | P&A bots |
| @mention para bot | Semelhante ao canal | Bots que contam as brincadeiras e fazem anotações |

### <a name="in-a-channel"></a>Em um canal

Os canais contêm conversas encadeadas entre várias pessoas até dois mil. Isso pode dar ao bot um grande alcance, mas as interações individuais devem ser concisas. Interações multi-turn tradicionais não funcionam. Em vez disso, você deve procurar usar cartões interativos ou módulos de tarefa ou mover a conversa para uma conversa um para um para coletar muitas informações. Seu bot só tem acesso a mensagens onde ele está `@mentioned`. Você pode recuperar mensagens adicionais da conversa usando Graph microsoft e permissões no nível da organização.

Os bots funcionam melhor em um canal nos seguintes casos:

* Notificações, onde você fornece um cartão interativo para os usuários receberem informações adicionais.
* Cenários de feedback, como pesquisas e pesquisas.
* Um único ciclo de solicitação ou resposta resolve interações e os resultados são úteis para vários membros da conversa.
* Bots sociais ou divertidos, onde você recebe uma imagem de gato incrível, escolhe aleatoriamente um vencedor e assim por diante.

### <a name="in-a-group-chat"></a>Em um chat em grupo

Os chats de grupo são conversas não-encadeadas entre três ou mais pessoas. Tendem a ter menos membros do que um canal e são mais temporários. Semelhante a um canal, seu bot só tem acesso a mensagens em que ele está `@mentioned` diretamente.

Nos casos em que os bots funcionam melhor em um canal também funcionam melhor em um chat em grupo.

### <a name="in-a-one-to-one-chat"></a>Em um chat um para um

O chat um para um é uma maneira tradicional de um bot de conversa interagir com um usuário. Alguns exemplos de bots de conversa um para um são:

* P&A bots
* bots que iniciam fluxos de trabalho em outros sistemas
* bots que contam as piadas
* bots que anotam Antes de criar chatbots um para um, considere se uma interface baseada em conversa é a melhor maneira de apresentar sua funcionalidade.

## <a name="disadvantages-of-bots"></a>Desvantagens dos bots

Uma caixa de diálogo extensa entre seu bot e o usuário é uma maneira lenta e complexa de concluir uma tarefa. Um bot que oferece suporte a comandos excessivos, especialmente uma ampla variedade de comandos, não é bem-sucedido ou exibido positivamente pelos usuários.

### <a name="have-multi-turn-experiences-in-chat"></a>Ter experiências multi-turn no chat

Uma caixa de diálogo extensa exige que o desenvolvedor mantenha o estado. Para sair desse estado, um usuário deve ter um tempo de vida ou selecionar **Cancelar**. Além disso, o processo é tedioso. Por exemplo, consulte o seguinte cenário de conversa:

USER: Agende uma reunião com Megan.

BOT: Eu descobri 200 resultados, inclua um nome e sobrenome.

USER: Agende uma reunião com Megan Bowen.

BOT: OK, a que horas você gostaria de se encontrar com Megan Bowen?

USER: 13:00 pm.

BOT: Em qual dia?

### <a name="support-too-many-commands"></a>Dar suporte a muitos comandos

Como há apenas seis comandos visíveis no menu de bot atual, é improvável que algo mais seja usado com qualquer frequência. Bots que vão fundo em uma área específica em vez de tentar ser um trabalho de assistente amplo e melhor tarifa.

### <a name="maintain-a-large-knowledge-base"></a>Manter uma grande base de dados de conhecimento

Uma das desvantagens dos bots é que é difícil manter uma grande base de dados de conhecimento de recuperação com respostas sem controle. Os bots são mais adequados para interações curtas e rápidas e não passam por listas longas procurando uma resposta.

## <a name="code-snippets"></a>Trechos de código

O código a seguir fornece um exemplo de atividade bot para um escopo de equipe de canal:

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

O código a seguir fornece um exemplo de atividade bot para um chat um para um:

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

|Nome do exemplo | Descrição | .NETCore | Node.js |
|----------------|-----------------|--------------|----------------|
| Bot de conversas do Teams | Manipulação de eventos de mensagens e conversas. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Manipuladores de atividade de bot](~/bots/bot-basics.md)

## <a name="see-also"></a>Confira também

* [Bots de chamadas e reuniões](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)
* [Conversas de bot](~/bots/how-to/conversations/conversation-basics.md)
* [Menus de comando bot](~/bots/how-to/create-a-bot-commands-menu.md)
* [Fluxo de autenticação para bots Microsoft Teams](~/bots/how-to/authentication/auth-flow-bot.md)
* [Usar módulos de tarefas dos bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
