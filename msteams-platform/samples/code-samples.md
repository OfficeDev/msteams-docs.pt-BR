---
title: Exemplos de código do Microsoft Teams
description: Links e descrições de exemplos de aplicativos para a plataforma de desenvolvedor do Microsoft Teams
keywords: Exemplos de desenvolvedor do Microsoft Teams
ms.openlocfilehash: eb7794e788f8eb39102ac874748e23d8621f281e
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672437"
---
# <a name="code-samples-for-the-microsoft-teams-developer-platform"></a>Exemplos de código para a plataforma de desenvolvedor do Microsoft Teams

Aqui, você encontrará uma lista de exemplos de código que demonstram vários recursos da plataforma de desenvolvimento do Microsoft Teams e como criar aplicativos para aproveitar esses recursos.

## <a name="getting-samples"></a>Obtendo exemplos

Para baixar nossos exemplos do GitHub:

1. Selecione um dos projetos listados abaixo e abra o projeto no GitHub.
2. Escolha o botão **clone ou download** e copie a URL
3. Abra um prompt de comando no diretório pai no qual você deseja instalar o projeto de exemplo
4. Sejam`git clone <pasted url>`

### <a name="for-netc-samples"></a>Para amostras .NET/C#

Cada um dos exemplos do .NET inclui um arquivo de solução do Visual Studio que pode criar a solução totalmente, incluindo a restauração dos pacotes do NuGet.

### <a name="for-nodejs-samples"></a>Para exemplos de Node. js

Fornecemos um arquivo Packages. JSON que lista todos os pacotes necessários para um exemplo. Basta executar `npm install` a partir da linha de comando no diretório do projeto Node. js para instalar os pacotes necessários. Agora você está pronto para abrir o projeto no Visual Studio Code e começar a experimentá-lo.

### <a name="for-other-samples"></a>Para outros exemplos

Como sempre, o arquivo LEIAme do projeto deve ter mais informações sobre necessidades específicas de exemplos específicos.

## <a name="get-started"></a>Introdução

| Amostra | Descrição|
|--------|-------------|
| [Olá mundo no Microsoft Teams com node. js](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) | Um exemplo de aplicativo do `Node.js` Teams na introdução aos recursos básicos do aplicativo.|
| [Olá mundo no Microsoft Teams com C# .NET](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) | Um exemplo de aplicativo do `C# .NET` Teams na introdução aos recursos básicos do aplicativo.|
| [Introdução ao gerador Yeoman para o Microsoft Teams](~/tutorials/get-started-yeoman.md) | Criar um aplicativo do teams a partir do zero usando o gerador Yeoman para o Microsoft Teams. |

## <a name="bots-using-the-v4-sdk"></a>Bots (usando o SDK v4)

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="messaging-extensions-using-the-v4-sdk"></a>Extensões de mensagens (usando o SDK v4)

| Amostra | Descrição | .NET Core | JavaScript |
|--------|------------- |---|---|
| Comando de pesquisa | Extensão de mensagens simples com um comando de pesquisa | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)| [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|
| Comando ação | Extensão de mensagens simples com um comando Action. Resposta inserida na área de mensagem de composição. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)|
| Comando Action com resposta de bot | Extensão de mensagens com um comando Action. Resposta inserida na conversa pelo bot. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/53.teams-messaging-extensions-action-preview)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/53.teams-messaging-extensions-action-preview)|
| Comando de pesquisa | extensão de mensagens com um comando de pesquisa e autenticação e configuração | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)| [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)|

## <a name="outgoing-webhooks"></a>WebHooks de saída

| Amostra | Descrição
|--------|-------------
| [Webhook de saída para C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook) | Ilustra como criar um **webhook de saída** para o Microsoft Teams em C#/.net.
| [Webhook de saída para node. js](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs) | Ilustra como criar um **webhook de saída** simples para o Microsoft Teams em aproximadamente 50 linhas de código node. js.

## <a name="connectors"></a>Conectores

| Amostra | Descrição
|--------|-------------
| [Conector de exemplo para node. js](https://github.com/OfficeDev/microsoft-teams-sample-connector-nodejs) | Este exemplo, escrito em node. js, demonstra como criar um conector para o Microsoft Teams usando o GitHub como um exemplo para gerar notificações de conector.
| [Exemplo de conector para C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-connector-csharp) | Este exemplo, escrito em C#, demonstra como criar um conector para o Microsoft Teams usando um exemplo de aplicativo de lista de tarefas como um exemplo para gerar notificações de conector.

## <a name="graph-api"></a>API do Graph

| Amostra | Descrição
|--------|-------------
| [Exemplos de API do Microsoft Graph](https://github.com/OfficeDev/microsoft-teams-sample-graph) | Estes exemplos demonstram o uso de chamadas da API do Microsoft Graph para executar tarefas como a consulta de equipes e canais de um serviço Web que está fora do Microsoft Teams.

## <a name="others"></a>Outros

| Código | Descrição |
|------|------------- |
| [Exemplo completo no node. js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) | Este exemplo mostra como usar todos os recursos da plataforma Microsoft Teams. Observação: Este exemplo usa o SDK da estrutura de bot v3.|
| [Exemplo completo em C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) | Este exemplo mostra como usar todos os recursos da plataforma Microsoft Teams. Observação: Este exemplo usa o SDK da estrutura de bot v3. |
| [Aplicativos de linha de negócios em C#/.NET](https://github.com/OfficeDev/msteams-sample-line-of-business-apps-csharp) | Este repositório contém vários exemplos de linha de aplicativos comerciais que podem ser usados para inspiração ou como modelos a serem criados na parte superior do. Observação: esses exemplos usam o SDK da estrutura de bot v3.|
| [Aplicativo de guia de amostra de lista de tarefas pendentes](https://github.com/OfficeDev/microsoft-teams-sample-todo) | Este exemplo de Node. js mostra como é fácil converter um aplicativo Web existente em uma guia. |
| [Orky](https://github.com/OfficeDev/Orky) | Você pode usar o Orky para registrar seu próprio bot local no Microsoft Teams e executar scripts de qualquer lugar! |
| [Compilação 2017 clima](https://github.com/OfficeDev/microsoft-teams-build2017-weather) | Atualizados. Código-fonte da sessão//compilar 2017 para adicionar uma guia de clima ao aplicativo esqueleto gerado anteriormente na sessão. |

### <a name="bot-framework-sdk-v3-samples"></a>Amostras do SDK da estrutura do bot v3

| Amostra | Descrição |
|--------|------------- |
| [Exemplo de bot para C#/.NET](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/CSharp/Samples/Microsoft.Bot.Connector.Teams.SampleBot) | Amostras do bot Framework v3|
| [Bot de amostra para node. js](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/Node/samples) | Amostras do bot Framework v3 |
