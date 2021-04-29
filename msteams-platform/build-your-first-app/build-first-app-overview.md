---
title: Começar - Criar sua primeira visão geral do aplicativo e pré-requisitos
author: girliemac
description: Saiba como começar com o desenvolvimento de aplicativos do Microsoft Teams e configurar seu ambiente.
ms.author: timura
ms.date: 03/18/2021
ms.topic: quickstart
ms.openlocfilehash: 3bc99c535ea659f046b65dc26d9a60de0dd49cab
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068561"
---
# <a name="get-started-with-microsoft-teams-app-development"></a>Começar com o desenvolvimento de aplicativos do Microsoft Teams

Crie um aplicativo simples para aprender as noções básicas do desenvolvimento de aplicativos do Teams. Depois de ver "Hello, World!", experimente qualquer um dos outros artigos de início para obter mais informações sobre ferramentas comuns, conceitos fundamentais e recursos avançados.



## <a name="what-youll-learn"></a>O que você aprenderá

* Obter e executar rapidamente com o teams Toolkit, uma extensão Visual Studio Código 
* Configurar seu aplicativo com o App Studio 
* Familiarizar-se com as ferramentas de desenvolvedor e os SDKs do Teams
* Considere conceitos importantes de aplicativos do Teams, como práticas recomendadas de autenticação e design

Você pode criar o aplicativo do Teams usando qualquer tecnologia de sua escolha, por exemplo, a interface de linha de comando (CLI). Porém, esses artigos ajudam você a começar a usar as seguintes ferramentas e tecnologias recomendadas:

* Teams Toolkit, uma extensão Visual Studio código
* React.js para guias
* Node.js para bots e extensões de mensagens


## <a name="teams-app-fundamentals"></a>Fundamentos do aplicativo teams

Você pode criar aplicativos personalizados do Teams para si mesmo, pessoas em sua organização ou pessoas em todo o mundo. Antes de começar, você deve entender os seguintes conceitos fundamentais sobre o desenvolvimento de aplicativos do Teams:

### <a name="common-app-use-cases"></a>Casos comuns de uso de aplicativo

Alguns cenários típicos com os que um aplicativo personalizado do Teams pode ajudar são:

* Incorporar conteúdo baseado na Web, como um aplicativo Web ou parte de um site, no cliente teams
* Procure informações rapidamente em outro sistema e adicione-as a uma conversa do Teams 
* Disparar fluxos de trabalho e processos diretamente do que é dito em uma conversa 

### <a name="app-capabilities-and-tools"></a>Recursos e ferramentas do aplicativo

Um aplicativo é feito de um ou mais recursos do Teams e pontos de interação do usuário. Seu toolset de desenvolvimento variará dependendo dos recursos que você deseja.

| **Recursos do aplicativo**| **Pontos de interação** | **Ferramentas recomendadas** | **SDKs** | **Pilhas de tecnologia** |
|--------|--------|--------|--------|--------|
| Guias | Espaços onde os usuários podem interagir com conteúdo da Web incorporado em contextos pessoais e compartilhados | Código VS com o Teams Toolkit extensão ou Gerador Yeoman | SDK do cliente JavaScript do Teams | Tecnologias web gerais (HTML, CSS e JavaScript) ou React.js |
| Bots | Chatbots que interagem com usuários em contextos pessoais e compartilhados | Código VS com o Teams Toolkit extensão ou Gerador Yeoman | Bot Franework SDK | Node.js, C# ou Python | 
| Extensões de mensagens | Atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem navegar para longe da conversa | Código VS com o Teams Toolkit extensão ou Gerador Yeoman | SDK da Estrutura de Bots | Node.js, C# ou Python |

### <a name="teams-doesnt-host-your-app"></a>O Teams não hospeda seu aplicativo

Quando um usuário instala seu aplicativo no Teams, ele só instala um pacote de aplicativos que contém um arquivo de configuração (também conhecido como manifesto do aplicativo) e os ícones do aplicativo. A lógica e o armazenamento de dados do aplicativo são hospedados em outro lugar, como os Serviços Web do Azure ou o localhost durante o desenvolvimento. O Teams acessa esses recursos por meio de HTTPS.

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="A ilustração mostrando seu aplicativo no Teams está apontando para a lógica do aplicativo no servidor de nuvem.":::

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar e executar seu primeiro aplicativo do Teams](../build-your-first-app/build-and-run.md)
