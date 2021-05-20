---
title: Comece - Construa sua primeira visão geral do aplicativo e pré-requisitos
author: girliemac
description: Aprenda a começar com Microsoft Teams desenvolvimento de aplicativos e configure seu ambiente.
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
# <a name="get-started-with-microsoft-teams-app-development"></a>Comece com o desenvolvimento de aplicativos Microsoft Teams

Construa um aplicativo simples para aprender o básico do desenvolvimento de aplicativos Teams. Uma vez que você vê "Olá, Mundo!", experimente qualquer um dos outros artigos para obter mais informações sobre ferramentas comuns, conceitos fundamentais e recursos avançados.



## <a name="what-youll-learn"></a>O que você vai aprender

* Levante-se e concorram rapidamente com o Teams Toolkit, uma extensão Visual Studio Code. 
* Configure seu aplicativo com App Studio.
* Conheça Teams ferramentas de desenvolvedores e SDKs.
* Considere conceitos importantes de aplicativos Teams, como autenticação e design de práticas recomendadas.

Você pode criar um aplicativo Teams usando qualquer tecnologia de sua escolha, por exemplo, interface de linha de comando (CLI). Mas, esses artigos ajudam você a começar com as seguintes ferramentas e tecnologias recomendadas:

* Teams Toolkit, uma extensão Visual Studio Code
* React.js para guias
* Node.js para bots e extensões de mensagens


## <a name="teams-app-fundamentals"></a>Teams fundamentos do aplicativo

Você pode criar aplicativos personalizados Teams para você, pessoas em sua organização ou pessoas em todo o mundo. Antes de começar, você deve entender os seguintes conceitos fundamentais sobre Teams desenvolvimento de aplicativos:

### <a name="common-app-use-cases"></a>Casos comuns de uso de aplicativos

Alguns cenários típicos que um aplicativo de Teams personalizado pode ajudar são:

* Incorpore conteúdo baseado na Web, como um aplicativo web ou parte de um site, no Teams cliente.
* Procure informações rapidamente em outro sistema e adicione-as a uma conversa Teams.
* Acione fluxos de trabalho e processos diretamente do que é dito em uma conversa.

### <a name="app-capabilities-and-tools"></a>Recursos e ferramentas do aplicativo

Um aplicativo é composto por um ou mais Teams recursos e pontos de interação do usuário. Seu lado de ferramentas de desenvolvimento vai variar dependendo dos recursos que você deseja.

| **Recursos do aplicativo**| **Pontos de interação** | **Ferramentas recomendadas** | **SDKs** | **Pilhas de tecnologia** |
|--------|--------|--------|--------|--------|
| Guias | Espaços onde os usuários podem interagir com conteúdo da Web incorporado em contextos pessoais e compartilhados. | VS Code com extensão Teams Toolkit ou Gerador Yeoman | SDK do cliente JavaScript do Teams | Tecnologias web gerais (HTML, CSS e JavaScript) ou React.js |
| Bots | Chatbots que interagem com os usuários em contextos pessoais e compartilhados. | VS Code com extensão Teams Toolkit ou Gerador Yeoman | Quadro de bot SDK | Node.js, C#ou Python | 
| Extensões de mensagens | Atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem navegar longe da conversa. | VS Code com extensão Teams Toolkit ou Gerador Yeoman | Quadro de bot SDK | Node.js, C#ou Python |

### <a name="teams-doesnt-host-your-app"></a>Teams não hospeda seu aplicativo

Quando um usuário instala seu aplicativo em Teams, ele só instala um pacote de aplicativo que contém um arquivo de configuração (também conhecido como manifesto de aplicativo) e os ícones do seu aplicativo. A lógica e o armazenamento de dados do seu aplicativo estão hospedados em outros lugares, como o Azure Web Services ou o localhost durante o desenvolvimento. Teams acessa esses recursos via HTTPS.

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Ilustração mostrando seu aplicativo em Teams está apontando para a lógica do aplicativo no servidor em nuvem.":::

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Construa e execute seu primeiro aplicativo de Teams](../build-your-first-app/build-and-run.md)
