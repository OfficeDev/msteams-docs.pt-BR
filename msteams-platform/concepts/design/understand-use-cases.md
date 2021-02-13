---
title: Compreender os casos de uso
author: clearab
description: Compreender os casos de uso
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 270771ecc47bbfc03a33d1603f680bc3424989ad
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231614"
---
# <a name="understand-your-use-cases"></a>Compreender os casos de uso

A plataforma do Microsoft Teams oferece uma grande variedade de pontos de [extensibilidade](~/concepts/extensibility-points.md) e elementos de interface do usuário que seu aplicativo pode tirar proveito. Se você ainda não tiver um bom entendimento do que é possível na plataforma do Teams, leia esse artigo primeiro.

Cada método de interação com seus usuários tem seus próprios pontos fortes e pontos fracos. Criar um aplicativo incrível do Teams é encontrar a combinação certa para atender às necessidades do usuário. Se você vai atender a essas necessidades, primeiro precisa entender essas necessidades.

## <a name="what-problem-are-you-trying-to-solve"></a>Que problema você está tentando resolver?

Todo bom aplicativo tem um problema principal (ou necessidade) que está tentando resolver. Antes de começar a criar, você precisa articular qual é o problema. No fundo, o Teams é uma plataforma de colaboração, portanto, os aplicativos que procuram resolver problemas de colaboração são um ótimo ajuste. Também é uma plataforma social, é na verdade plataforma cruzada, fica no centro do Office 365 e oferece uma tela pessoal para você criar aplicativos. Há uma enorme variedade de necessidades que podem ser resolvidas com um aplicativo do Teams, mas certifique-se de entender qual delas você está tentando resolver.

## <a name="who-are-you-solving-it-for"></a>Para quem você está resolvendo isso?

Às vezes, isso pode ser óbvio: "O sistema de monitoramento da minha equipe precisa enviar alertas em algum lugar, precisamos poder falar sobre eles muito rapidamente e nenhum de nós deseja verificar nosso email". Às vezes, seu público-alvo pode crescer ao longo do tempo: "Nossa equipe de equipe está realmente certa do nosso sistema de alertas e agora quer entrar em ação". Entender quem são seus usuários o ajudará a identificar o modelo de distribuição certo, mas o mais importante o ajudará a identificar *como eles usam o Teams.* Eles são principalmente trabalhadores de linha de frente em clientes móveis? Você espera que muitos usuários convidados precisem acessar seu aplicativo? Eles usam equipes e canais ou principalmente chats em grupo? Quão tecnicamente sofisticados eles são? Você precisará de uma experiência de adoção completa ou alguns ponteiros precisarão?

Às vezes, a resposta é "Queremos resolver esse problema para todos os usuários do Team em todos os lugares". Se esse for o caso para você, você vai querer gastar algum tempo entendendo o que é necessário para ser [publicado no AppSource](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md).

## <a name="do-you-need-authentication"></a>Você precisa de autenticação?

Você deve identificar logo no início se precisará proteger os serviços que está expondo e em que nível. Lembre-se de que os serviços Web que você exporá em seu aplicativo do Teams estão disponíveis publicamente pela Internet, portanto, se você precisar proteger-los, comece a pensar sobre como agora.

## <a name="should-the-entire-app-be-in-teams"></a>O aplicativo inteiro deve estar no Teams?

Se você estiver criando algo totalmente novo ou trazendo uma solução existente para o Teams, é importante decidir se o aplicativo inteiro estará dentro do cliente do Teams ou se faz sentido trazer apenas uma parte da experiência. Com uma combinação de guias, extensões de mensagens, módulos de tarefas, cartões interativos e bots de conversa, você pode criar aplicativos complexos completamente dentro do Teams. No entanto, isso nem sempre faz sentido. Lembre-se de quem são seus usuários e o problema que você está tentando resolver. Eles já têm um sistema para resolver a maioria do problema, e você só precisa estender um subconjunto da funcionalidade para o Teams? Normalmente, se você vai trazer apenas uma parte da sua solução, deve se concentrar no compartilhamento, colaboração e inicialização e monitoramento de fluxos de trabalho.

## <a name="what-will-the-onboarding-experience-be-like"></a>Como será a experiência de integração?

Sua experiência de integração pode ser a diferença entre o sucesso ou a falha do seu aplicativo. Para cada funcionalidade do seu aplicativo e para cada contexto em que essa funcionalidade pode ser instalada, você deve ter um plano de como você vai se apresentar. A maneira como você apresenta seu bot de conversa quando ele é instalado em um canal com milhares de pessoas provavelmente será diferente de quando ele é instalado em um chat de uma para uma. O que acontece quando um usuário configura sua guia pela primeira vez em um canal? Se você estiver compartilhando cartões com uma extensão de mensagens, faz sentido adicionar um link pequeno a uma página "saiba mais" para ajudar a apresentar aos usuários o que mais seu aplicativo pode fazer?

Saber quem são seus usuários ajudará você a criar a experiência certa. Você espera que a maioria das pessoas já tenha algum contexto sobre o que é seu aplicativo ou já tenha usado seus serviços em outro contexto? Ou eles chegarão ao seu aplicativo sem conhecimento prévio? Crie sua experiência de integração com seus principais usuários em mente.

Lembre-se também de que os usuários podem descobrir seu aplicativo de várias maneiras: eles podem ser aqueles que o instalam ou podem ser introduzidos em seu aplicativo quando outro membro da equipe o usa para compartilhar conteúdo. Se você quiser que seu aplicativo seja distribuído, procure formas de se apresentar para todos.

Acima de tudo, lembre-se de que ninguém gosta de spam. É uma boa maneira de deixar de instalar mensagens pessoais e de canal rapidamente!

## <a name="next-steps"></a>Próximas etapas

* [Mapear seus casos de uso para a funcionalidade](~/concepts/design/map-use-cases.md)
* [Escolha como distribuir o aplicativo](../deploy-and-publish/overview.md)

## <a name="learn-more"></a>Saiba Mais

* [Criar guias efetivas](~/tabs/design/tabs.md)
* [Criar bots incríveis](~/bots/design/bots.md)

