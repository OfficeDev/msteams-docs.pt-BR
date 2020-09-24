---
title: Exemplos de código do Microsoft Teams
description: Links e descrições de exemplos de aplicativos para a plataforma de desenvolvedor do Microsoft Teams
keywords: Exemplos de desenvolvedor do Microsoft Teams
ms.openlocfilehash: 7a81494d7808c27c495c660b5d58f7779ba87c83
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237955"
---
# <a name="tutorials-and-code-samples-for-the-microsoft-teams-developer-platform"></a>Tutoriais e exemplos de código para a plataforma de desenvolvedor do Microsoft Teams

Aqui, você encontrará uma lista de tutoriais e exemplos de código que demonstram como você pode estender os recursos da plataforma de desenvolvedor do teams criando aplicativos personalizados.

## <a name="getting-started-with-microsoft-learn"></a>Introdução ao Microsoft Learn

| Recursos| Módulo de aprendizado|
|--------|-------------|
| Guias — experiências da Web incorporadas  |  [Criar experiências da Web incorporadas com guias do Microsoft Teams](https://docs.microsoft.com/learn/modules/embedded-web-experiences/) |
| Webhooks e conectores  |  [Conectar serviços Web ao Microsoft Teams com WebHooks e conectores do Office 365](https://docs.microsoft.com/learn/modules/msteams-webhooks-connectors/) |
|Extensões de mensagens  | [Interações orientadas a tarefas no Microsoft Teams com extensões de mensagens](https://docs.microsoft.com/learn/modules/msteams-messaging-extensions/)  |
| Módulos de tarefas |  [Coletar entrada no Microsoft Teams com módulos de tarefa](https://docs.microsoft.com/learn/modules/msteams-task-modules/) |
| Bots de conversa  | [Criar bots de conversas interativas para o Microsoft Teams](https://docs.microsoft.com/learn/modules/msteams-conversation-bots/)  |

## <a name="getting-started-with-code-samples"></a>Introdução aos exemplos de código

Para baixar nossos exemplos do GitHub:

1. Selecione um dos projetos listados abaixo e abra o projeto no GitHub.
2. Escolha o botão **clone ou download** e copie a URL
3. Abra um prompt de comando no diretório pai no qual você deseja instalar o projeto de exemplo
4. Sejam `git clone <pasted url>`

### <a name="for-netc-samples"></a>Para amostras .NET/C#

Cada um dos exemplos do .NET inclui um arquivo de solução do Visual Studio que pode criar a solução totalmente, incluindo a restauração dos pacotes do NuGet.

### <a name="for-nodejs-samples"></a>Para obter Node.js amostras

Fornecemos um packages.jsno arquivo que lista todos os pacotes necessários para um exemplo. Basta executar a `npm install` partir da linha de comando em seu diretório de Node.js projeto para instalar os pacotes necessários. Agora você está pronto para abrir o projeto no Visual Studio Code e começar a experimentá-lo.

### <a name="for-other-samples"></a>Para outros exemplos

Como sempre, o arquivo LEIAme do projeto deve ter mais informações sobre necessidades específicas de exemplos específicos.

## <a name="bots-using-the-v4-sdk"></a>Bots (usando o SDK v4)

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

>[!TIP]
>Visite o [repositório de exemplos da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples) para exibir os exemplos de SDK do Microsoft bot Framework v4 centrados em tarefas para C#, JavaScript, TypeScript e Python.

## <a name="messaging-extensions-using-the-v4-sdk"></a>Extensões de mensagens (usando o SDK v4)

| Amostra | Descrição | .NET Core | JavaScript | Python|
|--------|------------- |---|---|----|
| Extensões de mensagens-pesquisa | Extensão de mensagens que aceita solicitações de pesquisa e retorna resultados. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |
| Extensões de mensagens-ação | Extensão de mensagens que aceita parâmetros e retorna um cartão. Além disso, como receber uma mensagem encaminhada como um parâmetro em uma extensão de mensagens. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/51.teams-messaging-extensions-action) |
| Extensões de mensagens-auth e config | A extensão de mensagens que tem uma página de configuração, aceita solicitações de pesquisa e retorna resultados após o usuário entrar. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) |
| Extensões de mensagens-visualização de ação | Demonstra como criar um fluxo de visualização e edição para uma extensão de mensagens. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/53.teams-messaging-extensions-action-preview) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/53.teams-messaging-extensions-action-preview) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/53.teams-messaging-extensions-action-preview) |
| Desenrolamento de link | Extensão de mensagens que executa o link Unfurling. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/55.teams-link-unfurling) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/55.teams-link-unfurling) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/55.teams-link-unfurling) |


## <a name="outgoing-webhooks"></a>WebHooks de saída

| Amostra | Descrição
|--------|-------------
| [Webhook de saída para C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook) | Ilustra como criar um **webhook de saída** para o Microsoft Teams em C#/.net.
| [Webhook de saída para Node.js](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs) | Ilustra como criar um **webhook de saída** simples para o Microsoft Teams em aproximadamente 50 linhas de código de Node.js.

## <a name="connectors"></a>Conectores

| Amostra | Descrição
|--------|-------------
| [Conector de amostra para Node.js](https://github.com/OfficeDev/microsoft-teams-sample-connector-nodejs) | Este exemplo, escrito em Node.js, demonstra como criar um conector para o Microsoft Teams usando o GitHub como um exemplo para gerar notificações de conector.
| [Exemplo de conector para C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-connector-csharp) | Este exemplo, escrito em C#, demonstra como criar um conector para o Microsoft Teams usando um exemplo de aplicativo de lista de tarefas como um exemplo para gerar notificações de conector.

## <a name="graph-api"></a>API do Graph

| Amostra | Descrição
|--------|-------------
| [Exemplos de API do Microsoft Graph](https://github.com/OfficeDev/microsoft-teams-sample-graph) | Estes exemplos demonstram o uso de chamadas da API do Microsoft Graph para executar tarefas como a consulta de equipes e canais de um serviço Web que está fora do Microsoft Teams.

### <a name="bot-framework-sdk-v3-samples"></a>Amostras do SDK da estrutura do bot v3

| Amostra | Descrição |
|--------|------------- |
| [Exemplo de bot para C#/.NET](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/CSharp/Samples/Microsoft.Bot.Connector.Teams.SampleBot) | Amostras do bot Framework v3|
| [Bot de amostra para Node.js](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/Node/samples) | Amostras do bot Framework v3 |
