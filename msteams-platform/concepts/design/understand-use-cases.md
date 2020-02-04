---
title: Entender seus casos de uso
author: clearab
description: Decidir como distribuir seu aplicativo
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: ef1007c21e79cd69155b64f02d2980bcf6a708b9
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672777"
---
# <a name="understand-your-use-cases"></a>Entender seus casos de uso

A plataforma Microsoft Teams oferece uma grande variedade de [pontos de extensibilidade e elementos de interface do usuário](~/concepts/extensibility-points.md) que o aplicativo pode aproveitar. Se você ainda não tem uma boa compreensão do que é possível na plataforma do Microsoft Teams, leia primeiro esse artigo.

Cada método de interação com seus usuários tem seus próprios pontos fortes e fracos. Criar um aplicativo do teams awesome é tudo sobre a localização da combinação certa para atender às necessidades do usuário. Se você for atender a essas necessidades, primeiro você precisará entendeu-las.

## <a name="what-problem-are-you-trying-to-solve"></a>Qual problema você está tentando resolver?

Todos os bons aplicativos têm um problema principal (ou precisam) ele está tentando resolver, antes de iniciar a construção, você precisa articular o problema. No coração, o Microsoft Teams é uma plataforma de colaboração, de forma que os aplicativos que procuram resolver problemas de colaboração são um ótimo ajuste. Também é uma plataforma social, que é nativamente entre plataformas, está no coração do Office 365 e oferece uma tela pessoal para você criar aplicativos. Há uma variedade incrivelmente grande de necessidades que podem ser resolvidas com um aplicativo do Microsoft Teams, apenas não deixe de compreender qual delas você está tentando resolver.

## <a name="who-are-you-solving-it-for"></a>Por quem você está resolvendo?

Às vezes, isso pode ser óbvio: "meu sistema de monitoramento de minha equipe precisa enviar alertas em algum lugar, precisamos discuti-los de forma realmente rápida e nenhum de nós queremos verificar nosso email." Às vezes, o público-alvo pode crescer ao longo do tempo: "nossa equipe irmã é realmente Jealous do nosso sistema de alertar e, agora, você já quer começar a agir." Entender quem seus usuários o ajudará a identificar o modelo de distribuição certo, mas o mais importante ajudará você a identificar *como eles usam o Microsoft Teams*. Eles são principalmente funcionários de linha de frente em clientes móveis? Você espera que muitos usuários convidados precisem de acesso ao seu aplicativo? Eles usam equipes e canais, ou basicamente agrupam chats? Como o tecnicamente é sofisticado? Você precisará de uma experiência de integração completa, ou alguns ponteiros o farão?

Às vezes, a resposta é "queremos resolver esse problema para todos os usuários da equipe em qualquer lugar". Se esse for o caso, você desejará levar algum tempo entendendo [o que é necessário para ser publicado no AppSource](~/concepts/deploy-and-publish/appsource/prepare/overview.md).

## <a name="do-you-need-authentication"></a>Você precisa de autenticação?

Você deve identificar o início, se for necessário proteger os serviços que você está expondo e em que nível. Lembre-se de que os serviços Web que você estará expondo no aplicativo do Microsoft Teams estão disponíveis publicamente pela Internet, portanto, se você precisar protegê-los, comece a pensar em como agora.

## <a name="should-the-entire-app-be-in-teams"></a>O aplicativo inteiro deve estar no Microsoft Teams?

Se você está criando algo totalmente novo ou trazendo uma solução existente para o Teams, é importante decidir se o aplicativo inteiro será dentro do cliente do teams ou se fizer sentido apenas realizar uma parte da experiência. Com uma combinação de guias, extensões de mensagens, módulos de tarefa, cartões interativos e bots de conversas, você pode criar aplicativos complexos totalmente dentro do teams. No entanto, isso nem sempre faz sentido. Lembre-se de quem são seus usuários e o problema que você está tentando resolver. Eles já têm um sistema para resolver a maior parte do problema e você só precisa estender um subconjunto da funcionalidade para o Microsoft Teams? Normalmente, se você estiver em apenas uma parte de sua solução, deverá se concentrar no compartilhamento, na colaboração e na inicialização e no monitoramento de fluxos de trabalho.

## <a name="what-will-the-onboarding-experience-be-like"></a>Qual será a experiência de integração?

Sua experiência de integração pode ser a diferença entre o sucesso ou falha de seu aplicativo. Para cada recurso do seu aplicativo, e para cada contexto em que o recurso pode ser instalado, você deve ter um plano de como você se apresentará. Como você apresenta o bot da conversa quando estiver instalado em um canal com mil pessoas provavelmente será diferente de quando ele for instalado em um chat de um-para-um. O que acontece quando um usuário configura pela primeira vez sua guia em um canal? Se você estiver compartilhando cartões com uma extensão de mensagens, faz sentido adicionar um pequeno link a uma página "Saiba mais" para ajudar a apresentar aos usuários o que mais seu aplicativo pode fazer?

Saber quem seus usuários poderá ajudá-lo a criar a experiência certa. Você espera que a maioria das pessoas já tenha algum contexto sobre o seu aplicativo ou já tenha usado seus serviços em outro contexto? Ou eles estão chegando ao seu aplicativo sem conhecimento prévio? Crie sua experiência de integração com os principais usuários em mente.

Lembre-se de que os usuários podem descobrir seu aplicativo de várias maneiras: eles podem ser aqueles que a instalam ou podem ser introduzidos para seu aplicativo quando outro membro da equipe o usa para compartilhar conteúdo. Se você quiser que seu aplicativo se espalhe, procure maneiras de se apresentar a todos.

Acima de tudo, lembre-se de que ninguém curti spam. A transmissão com mensagens pessoais e de canal é uma boa maneira de ser desinstalado rapidamente!

## <a name="next-steps"></a>Próximas etapas

* [Mapear seus casos de uso para a funcionalidade](~/concepts/design/map-use-cases.md)
* [Escolha como distribuir seu aplicativo](~/concepts/deploy-and-publish/apps-publish.md)

## <a name="learn-more"></a>Saiba mais

* [Projetar guias eficazes](~/tabs/design/tabs.md)
* [Criar bots incríveis](~/bots/design/bots.md)

