---
title: Compreender os casos de uso
author: clearab
description: Compreender os casos de uso
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: a873c3030ee4ed5f5fc98229c058583e64c38de5
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654276"
---
# <a name="understand-your-use-cases"></a>Compreender os casos de uso

A plataforma do Microsoft Teams oferece uma grande variedade de pontos de entrada e elementos [de interface](../../concepts/extensibility-points.md) do usuário que seu aplicativo pode aproveitar.
> [!NOTE]
> Antes de começar a criar seus casos de uso, você deve ter uma boa compreensão dos recursos do Teams e do que é possível na plataforma do Teams usá-los.

Cada método de interação com seus usuários tem seus pontos fortes e fracos. Criar um aplicativo do Teams incrível é encontrar a combinação certa para atender às necessidades do usuário. Se você vai atender a essas necessidades, primeiro você precisa entender.

## <a name="understand-the-problem"></a>Entender o problema

Cada aplicativo bom tem um problema principal ou uma necessidade que está tentando resolver. Antes de começar a criar um aplicativo, você precisa articular qual é esse problema. No fundo, o Teams é uma plataforma de colaboração, portanto, os aplicativos que fazem pontes na conquista de uma colaboração eficaz são um ótimo ajuste. Também é uma plataforma social, é nativamente entre plataformas, fica no centro do Office 365 e oferece uma tela pessoal para você criar aplicativos. Nesta plataforma social, há uma ampla variedade de necessidades que podem ser resolvidas com um aplicativo do Teams. Você pode resolver uma ampla variedade de problemas, desde que entenda qual está tentando resolver. Antes de começar a criar um aplicativo, faça perguntas relevantes, como:

* Quais são os prós e contras do sistema de estado atual usados pelos usuários?
* Quais são os pontos de dor que seus usuários enfrentam a partir de hoje que você deseja resolver?
* Quais recursos ou recursos seus usuários gostam e adoram na maneira atual de fazer o processo?

## <a name="understand-your-user"></a>Entender seu usuário

Entenda quem é seu usuário e você pode identificar o modelo de distribuição correto, mas, mais importante, ele ajuda você a identificar como os usuários usam o Teams. Faça perguntas relevantes, como:

* Os usuários são principalmente trabalhadores de linha de frente em clientes móveis?
* Você espera que muitos usuários convidados precisem de acesso ao seu aplicativo?
* Eles usam equipes e canais ou principalmente chats de grupo?
* Quão tecnicamente sofisticados são seus usuários principais?
* Você precisa de uma experiência de integração completa ou alguns ponteiros podem fazer?

Às vezes, a resposta *é: queremos resolver esse problema para todos os usuários do Teams* em todos os lugares. Se esse for o caso para você, passe algum tempo compreendendo o que é necessário [para ser publicado no AppSource](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md).

## <a name="understand-the-limitations-of-the-app"></a>Compreender as limitações do aplicativo

Conhecer as limitações dos aplicativos em termos de acessibilidade de dados e requisitos de residência de dados ajudará você a projetar aplicativos melhores. Isso é importante, pois ter informações sobre quem é o proprietário dos dados e a disponibilidade de APIs afeta a arquitetura da solução. Novamente, faça perguntas relevantes, como:

* Quais são os desafios com a integração de back-end do aplicativo atual?
* Quem é o proprietário dos dados de back-end? In-house ou third-party.
* Há firewalls que impactam o funcionamento do aplicativo?
* Há APIs para acessar os dados necessários para o funcionamento do seu aplicativo? 

## <a name="provide-authentication"></a>Fornecer autenticação

Você deve identificar desde o início se precisar proteger os serviços que está expondo e em que nível. Lembre-se de que os serviços Web expostos em seu aplicativo do Teams estão disponíveis publicamente pela Internet. Portanto, se você precisar proteger eles, comece a pensar sobre isso agora. Se você precisar de uma solução que exija que você forneça acesso de convidados para usuários fora do locatário, as restrições e permissões de acesso precisam ser colocadas para proteger informações confidenciais. Você precisará projetar aplicativos considerando as limitações que vêm com o acesso do usuário convidado. Portanto, faça perguntas, como: 

* Os usuários acessarão diferentes exibições de dados com base em suas funções?
* Há PII envolvido?
* As interações também serão baseadas nas funções do usuário?
* Os usuários externos acessarão o aplicativo?

## <a name="decide-what-goes-in-teams"></a>Decidir o que acontece no Teams

Se você está criando algo novo ou trazendo uma solução existente para o Teams, é importante decidir se o aplicativo inteiro estará dentro do cliente do Teams. Verifique se faz sentido trazer apenas uma parte da experiência. Com uma combinação de guias, extensões de mensagens, módulos de tarefas, Cartões Adaptáveis e bots de conversação, você pode criar aplicativos complexos completamente no Teams.
Lembre-se de quem são seus usuários e do problema que você está tentando resolver. Eles já têm um sistema para resolver a maioria do problema ou você só precisa estender um subconjunto da funcionalidade para o Teams? Normalmente, se você vai trazer uma parte da solução, deve se concentrar em compartilhar, colaborar, iniciar e monitorar fluxos de trabalho.

## <a name="plan-the-onboarding-experience"></a>Planejar a experiência de integração

Sua experiência de integração pode ser a diferença entre sucesso ou falha para seu aplicativo. Para cada funcionalidade do seu aplicativo e cada contexto em que a funcionalidade pode ser instalada, você deve ter um plano para como você vai se apresentar. A maneira como você introduz o bot de conversa quando ele é instalado em um canal com milhares de pessoas, é diferente quando ele é instalado em um chat um para um. O que acontece quando um usuário configura sua guia pela primeira vez em um canal? Se você estiver compartilhando cartões com uma extensão de mensagens, faz sentido adicionar um pequeno link **a** uma página saiba mais para ajudar a apresentar aos usuários o que mais seu aplicativo pode fazer?

Saber quem são seus usuários ajuda você a criar a experiência certa. Você espera que a maioria das pessoas já tenha algum contexto do seu aplicativo ou já tenha usado seus serviços em outro contexto? Eles estão chegando ao seu aplicativo sem conhecimento prévio? Crie sua experiência de integração com seus principais usuários em mente.

Lembre-se de que os usuários podem descobrir seu aplicativo de várias maneiras. Eles podem ser os que o instalam ou podem ser introduzidos em seu aplicativo quando outro usuário o usa para compartilhar conteúdo. Se você quiser que mais usuários usem seu aplicativo, procure maneiras de se apresentar a todos.

Acima de tudo, lembre-se de que ninguém gosta de spam. A explosão com mensagens pessoais e de canal é uma boa maneira de não ser instalada rapidamente!

## <a name="plan-for-the-future"></a>Planejar o futuro

Identifique quais novos recursos o usuário preferirá ter na solução atual. Se você tiver um roteiro para adicionar novos recursos ao aplicativo, o design e a arquitetura serão afetados.

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Escolha como distribuir o aplicativo](../deploy-and-publish/overview.md)

> [!div class="nextstepaction"]
> [Projetar guias efetivas](../../tabs/design/tabs.md)

> [!div class="nextstepaction"]
> [Projetar bots incríveis](../../bots/design/bots.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mapear seus casos de uso](../../concepts/design/map-use-cases.md)
