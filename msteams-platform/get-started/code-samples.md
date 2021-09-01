---
title: Exemplos de código de aplicativo
description: Links e descrições de aplicativos de exemplo para a plataforma Microsoft Teams desenvolvedor
localization_priority: Normal
ms.topic: reference
keywords: Microsoft Teams exemplos de desenvolvedor
ms.openlocfilehash: c261aebc327d09265db8831c2b7a8549f30a34fe
ms.sourcegitcommit: 68f5411f5989ac706b6a4a7b2884296e145fe7c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2021
ms.locfileid: "58849423"
---
# <a name="overview"></a>Visão Geral

Neste tutorial, você aprenderá a criar um aplicativo usando React, Blazor, SPFx, C# ou .NET, Node.js e Gerador Yeoman. Você também aprenderá a criar seu primeiro bot e extensão de mensagens. Este tutorial levará você por meio de vários Exemplos de Código para Guias, Bots, Extensões de Mensagens, Webhooks e Conectores e APIs Graph que ajudarão você a personalizar e configurar seus aplicativos. Além disso, você também pode consultar as seções do Microsoft Learn nas quais você pode estender os recursos da plataforma de desenvolvedor Teams criando aplicativos personalizados.  

## <a name="getting-started-with-microsoft-learn"></a>Como começar com o Microsoft Learn

| **Recursos**| **Módulo Learn**|
|--------|-------------|
| Guias — experiências da Web incorporadas  |  [Crie experiências da Web incorporadas com guias do Microsoft Teams](/learn/modules/embedded-web-experiences/) |
| Webhooks e conectores  |  [Conecte os serviços da Web ao Microsoft Teams com webhooks e Conectores do Office 365](/learn/modules/msteams-webhooks-connectors/) |
|Extensões de mensagens  | [Interações orientadas por tarefas no Microsoft Teams com extensões de mensagens](/learn/modules/msteams-messaging-extensions/)  |
| Módulos de tarefas |  [Coletar entrada em Microsoft Teams com Módulos de Tarefa](/learn/modules/msteams-task-modules/) |
| Bots de conversa  | [Criar bots interativos de conversas para o Microsoft Teams](/learn/modules/msteams-conversation-bots/)  |

## <a name="build-your-first-microsoft-teams-app-overview"></a>Criar sua primeira visão geral Microsoft Teams aplicativo

Nas **lições de início,** você aprende a criar aplicativos Teams básicos. Cada tutorial mostra como criar um aplicativo simples e Teams do mundo real enquanto apresenta ferramentas comuns, conceitos fundamentais e recursos mais avançados.

### <a name="teams-app-fundamentals"></a>Teams básicos do aplicativo

A [Teams de desenvolvedor permite](../overview.md) que você crie aplicativos personalizados. Alguns cenários comuns em que um aplicativo Microsoft Teams personalizado pode ajudar são:

* Incorporar seu site ou aplicativo Web diretamente no cliente do Teams.
* Ajude os usuários a procurar rapidamente informações em outro sistema e adicionar os resultados a uma conversa em Teams.
* Acionar fluxos de trabalho e processos com base em uma conversa no Teams, preservando o contexto da conversa.

Antes de começar os tutoriais, você deve saber o seguinte sobre como criar aplicativos para Teams.

### <a name="app-capabilities"></a>Recursos do aplicativo

Um Teams app é feito de um ou mais recursos de [plataforma](../concepts/capabilities-overview.md) e pontos de interação [do usuário.](../concepts/extensibility-points.md)

Dependendo dos recursos que você deseja para seu aplicativo, você precisará de um toolset de desenvolvimento apropriado.

| Recursos do aplicativo | Interações do usuário | Ferramentas recomendadas | SDKs | Pilhas de tecnologia |
|--------|-------------|--------|--------|--------|
| Guias | Uma experiência da Web incorporada em tela inteira. | VS Code com Teams Toolkit ou YoTeams (Gerador Yeoman) | [Teams SDK do cliente](/javascript/api/overview/msteams-client) | Tecnologia Web em geral, HTML, CSS e JavaScript |
| Bots | Um bot de chat que conversa com membros. | VS Code com Teams Toolkit ou YoTeams (Gerador Yeoman) | [SDK da Estrutura de Bots](https://dev.botframework.com/) | Node.js, C# ou Python |
| Extensões de mensagens | Atalhos para inserir conteúdo externo em uma conversa ou tomar medidas em mensagens. | VS Code com Teams Toolkit ou YoTeams (Gerador Yeoman) | [SDK da Estrutura de Bots](https://dev.botframework.com/) | Node.js, C# ou Python |

A seção Começar levará você por meio de conjuntos de ferramentas recomendados e tecnologias comumente usadas, como Visual Studio Code com extensão Teams, React.js para guias e Node.js para bots e extensões de mensagens, embora você não se limite a usar essas pilhas *específicas.*

Se você preferir usar uma interface de linha de comando (CLI), consulte [create your first Microsoft Teams app using the Yeoman generator](../get-started/get-started-yeoman.md).

### <a name="teams-does-not-host-your-app"></a>Teams não hospeda seu aplicativo

Você instalará apenas um pacote de aplicativo que contém um arquivo de configuração, chamado de ícones de manifesto e aplicativo para Teams cliente. O restante das lógicas do aplicativo e o armazenamento de dados são hospedados em outro lugar, como os Serviços Web do Azure. Seu aplicativo na nuvem ou no localhost durante seu desenvolvimento acessa Teams via HTTPS.

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Ilustração mostrando seu aplicativo no Teams está apontando para a lógica do aplicativo no servidor de nuvem.":::

## <a name="see-also"></a>Confira também

* [Criar um aplicativo usando React](first-app-react.md)
* [Criar um aplicativo usando o Blazor](first-app-blazor.md)
* [Criar um aplicativo usando SPFx](first-app-spfx.md)
* [Criar um aplicativo usando C# ou .NET](get-started-dotnet-app-studio.md)
* [Criar um aplicativo usando o Node.js](get-started-nodejs-app-studio.md)
* [Criar um aplicativo usando o gerador Yeoman](get-started-yeoman.md)
* [Criar um programa bot de conversação](first-app-bot.md)
* [Criar uma extensão de mensagem](first-message-extension.md)
* [Exemplos de código](https://github.com/OfficeDev/Microsoft-Teams-Samples)
