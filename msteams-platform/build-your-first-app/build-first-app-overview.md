---
title: Começar - Criar sua primeira visão geral do aplicativo e pré-requisitos
author: girliemac
description: Saiba como começar a Microsoft Teams desenvolvimento de aplicativos e configurar seu ambiente.
ms.author: timura
ms.date: 03/18/2021
ms.topic: quickstart
ms.openlocfilehash: dae942be9383ef1e0a931d238e6148651f334ef5
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565876"
---
# <a name="get-started-with-microsoft-teams-app-development"></a>Começar com o desenvolvimento Microsoft Teams aplicativos

Crie um aplicativo simples para aprender as noções básicas Teams desenvolvimento de aplicativos. Depois de ver "Hello, World!", experimente qualquer um dos outros artigos de início para obter mais informações sobre ferramentas comuns, conceitos fundamentais e recursos avançados.



## <a name="what-youll-learn"></a>O que você aprenderá

* Obter e executar rapidamente com o Teams Toolkit, uma extensão Visual Studio Code de usuário. 
* Configure seu aplicativo com o App Studio.
* Familiarizar-se com Teams de desenvolvedor e SDKs.
* Considere conceitos Teams aplicativos importantes, como as práticas recomendadas de autenticação e design.

Você pode criar um aplicativo Teams usando qualquer tecnologia de sua escolha, por exemplo, a cli (interface de linha de comando). Porém, esses artigos ajudam você a começar a usar as seguintes ferramentas e tecnologias recomendadas:

* Teams Toolkit, uma extensão Visual Studio Code de dados
* React.js para guias
* Node.js para bots e extensões de mensagens


## <a name="teams-app-fundamentals"></a>Teams básicos do aplicativo

Você pode criar aplicativos Teams personalizados para si mesmo, pessoas em sua organização ou pessoas em todo o mundo. Antes de começar, você deve entender os seguintes conceitos fundamentais sobre Teams desenvolvimento de aplicativos:

### <a name="common-app-use-cases"></a>Casos comuns de uso de aplicativo

Alguns cenários típicos que um aplicativo Teams personalizado pode ajudar são:

* Incorporar conteúdo baseado na Web, como um aplicativo Web ou parte de um site, no Teams cliente.
* Procure informações rapidamente em outro sistema e adicione-as a uma Teams conversa.
* Aciona fluxos de trabalho e processos diretamente do que é dito em uma conversa.

### <a name="app-capabilities-and-tools"></a>Recursos e ferramentas do aplicativo

Um aplicativo é feito de um ou mais recursos Teams pontos de interação do usuário. Seu toolset de desenvolvimento variará dependendo dos recursos que você deseja.

| **Recursos do aplicativo**| **Pontos de interação** | **Ferramentas recomendadas** | **SDKs** | **Pilhas de tecnologia** |
|--------|--------|--------|--------|--------|
| Guias | Espaços onde os usuários podem interagir com conteúdo da Web incorporado em contextos pessoais e compartilhados. | VS Code com Teams Toolkit ou Gerador Yeoman | SDK do cliente JavaScript do Teams | Tecnologias web gerais (HTML, CSS e JavaScript) ou React.js |
| Bots | Chatbots que interagem com usuários em contextos pessoais e compartilhados. | VS Code com Teams Toolkit ou Gerador Yeoman | SDK da Estrutura de Bots | Node.js, C# ou Python | 
| Extensões de mensagens | Atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem navegar para longe da conversa. | VS Code com Teams Toolkit ou Gerador Yeoman | SDK da Estrutura de Bots | Node.js, C# ou Python |

### <a name="teams-doesnt-host-your-app"></a>Teams não hospeda seu aplicativo

Quando um usuário instala seu aplicativo no Teams, ele só instala um pacote de aplicativos que contém um arquivo de configuração (também conhecido como manifesto do aplicativo) e os ícones do aplicativo. A lógica e o armazenamento de dados do aplicativo são hospedados em outro lugar, como os Serviços Web do Azure ou o localhost durante o desenvolvimento. Teams acessa esses recursos por meio de HTTPS.

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Ilustração mostrando seu aplicativo no Teams está apontando para a lógica do aplicativo no servidor de nuvem.":::

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar e executar seu primeiro Teams aplicativo](../build-your-first-app/build-and-run.md)
