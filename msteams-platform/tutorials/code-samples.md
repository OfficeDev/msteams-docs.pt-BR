---
title: Exemplos de código do Microsoft Teams
description: Links e descrições de aplicativos de exemplo para a plataforma de desenvolvedores do Microsoft Teams
keywords: Exemplos de desenvolvedor do Microsoft Teams
ms.openlocfilehash: 665d3565f4f453d263fef6a17cb27f5060111468
ms.sourcegitcommit: 6d9c60cce1f2e5204e680c074ce77a8376233b59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49912313"
---
# <a name="tutorials-and-code-samples-for-the-microsoft-teams-developer-platform"></a>Tutoriais e exemplos de código para a plataforma de desenvolvedor do Microsoft Teams

Aqui você encontrará uma lista de tutoriais e exemplos de código que demonstram como você pode estender os recursos da plataforma de desenvolvedores do Teams criando aplicativos personalizados.

## <a name="getting-started-with-microsoft-learn"></a>Getting started with Microsoft Learn

| Recursos| Módulo Learn|
|--------|-------------|
| Guias — experiências da Web incorporadas  |  [Criar experiências da Web incorporadas com guias para o Microsoft Teams](https://docs.microsoft.com/learn/modules/embedded-web-experiences/) |
| Webhooks e conectores  |  [Conectar serviços Web ao Microsoft Teams com webhooks e Conectores do Office 365](https://docs.microsoft.com/learn/modules/msteams-webhooks-connectors/) |
|Extensões de mensagens  | [Interações orientadas a tarefas no Microsoft Teams com extensões de mensagens](https://docs.microsoft.com/learn/modules/msteams-messaging-extensions/)  |
| Módulos de tarefas |  [Coletar entrada no Microsoft Teams com módulos de tarefa](https://docs.microsoft.com/learn/modules/msteams-task-modules/) |
| Bots de conversa  | [Criar bots interativos de conversa para o Microsoft Teams](https://docs.microsoft.com/learn/modules/msteams-conversation-bots/)  |

## <a name="getting-started-with-code-samples"></a>Getting started with code samples

Para baixar nossos exemplos do GitHub:

1. Selecione um dos projetos listados abaixo e abra o projeto no GitHub.
2. Escolha o **botão Clonar ou baixar** e copie a URL
3. Abra um prompt de comando no diretório pai no qual você deseja instalar o projeto de exemplo
4. Executar `git clone <pasted url>`

### <a name="for-netc-samples"></a>Para exemplos de .NET/C#

Cada um dos nossos exemplos .NET inclui um arquivo de solução do Visual Studio que pode criar a solução totalmente, incluindo a restauração dos pacotes NuGet.

### <a name="for-nodejs-samples"></a>Para Node.js exemplos

Fornecemos um packages.jsno arquivo que lista todos os pacotes necessários para um exemplo. Basta executar `npm install` a partir da linha de comando no Node.js diretório do projeto para instalar os pacotes necessários. Agora você está pronto para abrir o projeto no Visual Studio Code e começar a experimentar.

### <a name="for-other-samples"></a>Para outros exemplos

Como sempre, o arquivo README do projeto deve ter mais informações sobre necessidades específicas para amostras específicas.

## <a name="bots-using-the-v4-sdk"></a>Bots (usando o SDK v4)

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

>[!TIP]
>Visite o [repositório de Exemplos](https://github.com/Microsoft/BotBuilder-Samples) da Estrutura de Bot para exibir exemplos voltados para tarefas do SDK do Microsoft Bot Framework v4 para C#, JavaScript, TypeScript e Python.

## <a name="messaging-extensions-using-the-v4-sdk"></a>Extensões de mensagens (usando o SDK v4)

| Amostra | Descrição | .NET Core | JavaScript | Python|
|--------|------------- |---|---|----|
| Extensões de mensagens - pesquisa | Extensão de mensagens que aceita solicitações de pesquisa e retorna resultados. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |
| Extensões de mensagens - ação | Extensão de mensagens que aceita parâmetros e retorna um cartão. Além disso, como receber uma mensagem encaminhada como um parâmetro em uma Extensão de Mensagens. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/51.teams-messaging-extensions-action) |
| Extensões de mensagens - auth e config | Extensão de mensagens que tem uma página de configuração, aceita solicitações de pesquisa e retorna resultados depois que o usuário se inscreva. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) |
| Extensões de mensagens - visualização de ação | Demonstra como criar um fluxo de Visualização e Edição para uma Extensão de Mensagens. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/53.teams-messaging-extensions-action-preview) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/53.teams-messaging-extensions-action-preview) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/53.teams-messaging-extensions-action-preview) |
| Desenrolamento de link | Extensão de mensagens que executa o link desesqueamento. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/55.teams-link-unfurling) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/55.teams-link-unfurling) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/55.teams-link-unfurling) |


## <a name="outgoing-webhooks"></a>Webhooks de saída

| Amostra | Descrição
|--------|-------------
| [Webhook de saída para C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook) | Ilustra como criar um **Webhook de** saída para o Microsoft Teams em C#/.NET.
| [Webhook de saída para Node.js](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs) | Ilustra como criar um **Webhook** de saída simples para o Microsoft Teams em cerca de 50 linhas Node.js código.

## <a name="connectors"></a>Conectores

| Amostra | Descrição
|--------|-------------
| [Conector de exemplo para Node.js](https://github.com/OfficeDev/microsoft-teams-sample-connector-nodejs) | Este exemplo, escrito em Node.js, mostra como criar um conector para o Microsoft Teams usando o GitHub como um exemplo para gerar notificações de conector.
| [Conector de exemplo para C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-connector-csharp) | Este exemplo, escrito em C#, mostra como criar um conector para o Microsoft Teams usando um aplicativo de lista de tarefas de exemplo como exemplo para gerar notificações de conector. Este exemplo também mostra como implementar a funcionalidade de logon na página de configuração do conector. 

## <a name="graph-api"></a>Graph API

| Amostra | Descrição
|--------|-------------
| [Exemplos de API do Microsoft Graph](https://github.com/OfficeDev/microsoft-teams-sample-graph) | Esses exemplos demonstram o uso de chamadas da API do Microsoft Graph para executar tarefas como consultar equipes e canais de um serviço Web em execução fora do Microsoft Teams.

### <a name="bot-framework-sdk-v3-samples"></a>Exemplos do SDK do Bot Framework v3

| Amostra | Descrição |
|--------|------------- |
| [Exemplo de bot para C#/.NET](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/CSharp/Samples/Microsoft.Bot.Connector.Teams.SampleBot) | Exemplos da Estrutura de Bot v3|
| [Exemplo de bot para Node.js](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/Node/samples) | Exemplos da Estrutura de Bot v3 |
