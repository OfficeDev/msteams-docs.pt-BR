---
title: Criando seu primeiro aplicativo de equipe
author: heath-hamilton
description: Tutorial para criar um aplicativo do Microsoft Teams real
ms.openlocfilehash: 4915dde4ef5a852f4fc5d1e4c83e3349db2eaf6b
ms.sourcegitcommit: 80bf79a952bb14cbc38c0bd1e3cf8a346158e28e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2020
ms.locfileid: "46655671"
---
# <a name="learn-how-to-build-your-first-teams-app"></a>Saiba como criar seu primeiro aplicativo do Microsoft Teams

Em **compilar seu primeiro aplicativo**, você aprende como criar um aplicativo Basic Teams por meio de tutoriais. As lições são criadas umas sobre as outras, orientando cada etapa de criação de um aplicativo simples e real de equipes do mundo. Apresentamos a você ferramentas comuns, conceitos fundamentais e links úteis ao longo do caminho.

Você começará a criar e executar um "Olá, mundo!" aplicativo de guia. Em seguida, você criará uma interface do usuário simples e aprenderá a obter um contexto útil com o SDK do JavaScript do Microsoft Teams.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
  >
  > - **Comece a trabalhar rapidamente com o Teams Toolkit**: o Microsoft Teams Toolkit para Visual Studio Code cuida da criação do seu projeto de aplicativo e do scaffolding, para que você possa ter um aplicativo em execução em minutos.
  > - **Defina seu aplicativo com o manifesto**: o manifesto é um plano gráfico onde você especifica os recursos e serviços que seu aplicativo Teams usa.
  > - **Escopo da sua audiência**: você pode criar um aplicativo do teams para uso pessoal ou colaboração. Nos tutoriais, você aprenderá como criar uma guia para usuários individuais ou um grupo de pessoas em um canal ou chat.
  > - Use o **SDK do teams para obter o contexto**: saiba como usar o SDK do Microsoft Teams JavaScript para executar a mudança de tema ou configurar a experiência de configuração  
  > - **Expanda em seu aplicativo**: em todos os tutoriais, nos links para tópicos relacionados que você provavelmente tem interesse (alguns dos quais incluem diretrizes de autenticação e Design).

## <a name="teams-app-fundamentals"></a>Conceitos básicos do aplicativo Teams

Antes de começar os tutoriais, você deve saber o seguinte sobre a criação de aplicativos para o Microsoft Teams.

### <a name="apps-can-have-multiple-capabilities"></a>Os aplicativos podem ter vários recursos

Os aplicativos do teams são compostos por um ou mais [recursos de plataforma](../capabilities-overview.md), incluindo [guias](../doc-links/what-are-tabs.md), [bots](../doc-links/what-are-bots.md ), [extensões de mensagens](../doc-links/what-are-messaging-extensions.md)e [conectores e WebHooks](../doc-links/what-are-webhooks-and-connectors.md). Os aplicativos do teams também têm muitas [convenções e elementos de interface do usuário](../doc-links/teams-ui-conventions.md), como cartões, módulos de tarefas e vinculação profunda, que você pode usar para criar a melhor experiência de usuário possível.

Para esses tutoriais, você criará apenas guias, mas poderá adicionar um bot ou outro recurso ao seu aplicativo como desejar.

### <a name="teams-doesnt-host-your-app"></a>O Microsoft Teams não hospeda seu aplicativo  

Um aplicativo do teams consiste em três partes principais:

1. O cliente Microsoft Teams (Web, desktop ou celular) onde os usuários interagem com seu aplicativo.
1. Seu aplicativo, serviço, fluxo de trabalho ou site que executa a lógica necessária, o armazenamento de dados e as chamadas de API para alimentar o aplicativo.
1. Seu pacote de aplicativos, que você usa para instalar o aplicativo no Teams. Ele contém metadados de aplicativo (nome, ícones, etc.) e aponta para seus serviços.

## <a name="next-step"></a>Próxima etapa

Isso é tudo por enquanto, vamos começar!

> [!div class="nextstepaction"]
> [Criar e executar seu primeiro aplicativo](build-and-run-with-toolkit.md)
