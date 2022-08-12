---
title: Perguntas para ajudar a planejar o desenvolvimento de aplicativos do Microsoft Teams
author: heath-hamilton
description: Perguntas a serem consideradas ao planejar seu aplicativo, entender seu usuário e suas necessidades, problemas que seu aplicativo resolve, autenticação do usuário e sua experiência de integração.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: surbhigupta
ms.openlocfilehash: 78dd40e13c3bdac359cc5201bda92a5b1daccfb8
ms.sourcegitcommit: 42602e8ec917f5033c0b6a95cf65b428db3c5b0a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2022
ms.locfileid: "67286116"
---
# <a name="teams-app-planning-checklist"></a>Lista de verificação de planejamento de aplicativos do Teams

O ciclo de vida de um aplicativo se estende desde o planejamento do aplicativo até a implantação e muito mais. É preciso mais do que conhecer seu usuário e seus requisitos para planejar seu aplicativo. Dependendo das necessidades do seu aplicativo, você também pode considerar o planejamento de futuras atualizações.

Vamos dar uma olhada prática no planejamento do ciclo de vida de um aplicativo.

## <a name="relevant-questions"></a>Perguntas relevantes

Aqui está uma lista de verificação de perguntas a serem consideradas ao planejar o aplicativo. Utilize-o como uma diretriz para garantir que seu plano cubra os detalhes importantes do desenvolvimento de aplicativos.

<br>
<br>
<details>
<summary>Entenda seu usuário</summary>

Entender o usuário e sua preocupação são os primeiros indicadores de como um aplicativo do Microsoft Teams pode ajudar. Construa seu caso de uso em torno do problema, determine como um aplicativo pode resolvê-lo e desenhe uma solução. Para obter mais informações, confira [entender seus casos de uso](understand-use-cases.md).

| # | Considere: |
| --- | --- |
| 1 | Os usuários são principalmente trabalhadores de linha de frente em clientes móveis? |
| 2 | Você espera que muitos usuários externos precisem de acesso ao seu aplicativo? |
| 3 | Eles usam equipes e canais ou principalmente chats em grupo? |
| 4 | Quão tecnicamente avançados são seus principais usuários? |
| 5 | Você precisa de uma experiência completa de integração ou algumas dicas podem ser suficientes? |

</details>
<br>
<details>
<summary>Entenda o problema</summary>

| # | Considere: |
|--- | --- |
| 1 | Quais são os prós e contras do sistema de estado atual usado pelos seus usuários? |
| 2 | Quais são os problemas enfrentados por seus usuários que você deseja resolver? |
| 3 | Quais recursos ou funcionalidades seus usuários gostam e adoram em sua maneira atual de fazer o processo? |

</details>
<br>
<details>
<summary>Entenda as limitações do aplicativo</summary>

| # | Considere: |
| --- | --- |
| 1 | Quais são os desafios com a integração de back-end do aplicativo atual? |
| 2 | Quem é o proprietário dos dados de back-end - internos ou terceiros? |
| 3 | Existem firewalls que afetam o funcionamento do aplicativo? |
| 4 | Existem APIs para acessar os dados necessários para o funcionamento do aplicativo? |

</details>
<br>
<details>
<summary>Fornecer autenticação</summary>

A autenticação se trata da validação de usuários de aplicativos e da proteção dos usuários do aplicativo e do aplicativo contra o acesso indevido. Você pode usar um método de autenticação adequado para seu aplicativo para validar os usuários do aplicativo que desejam usar o aplicativo do Teams. Para obter mais informações, confira [autenticar usuários no Microsoft Teams](../authentication/authentication.md).

| # | Considere:|
|--- | --- |
| 1 | Os usuários acessarão diferentes visualizações de dados com base nas suas funções? |
| 2 | Há conteúdo do cliente envolvido? |
| 3 | As interações também serão baseadas nas funções do usuário? |
| 4 | Usuários externos acessarão o aplicativo? |

</details>
<br>
<details>
<summary>Planeje a experiência de integração</summary>

Criar um aplicativo incrível do Teams tem tudo a ver com encontrar a combinação certa de recursos para atender às necessidades do usuário. Para fornecer aos usuários uma experiência de integração perfeita, você pode criar um guia passo a passo explicando como e o que fazer com seu aplicativo. Por exemplo, confira [criar um bot de conversa do Teams](../../sbs-teams-conversation-bot.yml).

| # | Considere: |
| --- | --- |
| 1 | O que acontece quando um usuário configura sua guia pela primeira vez em um canal? |
| 2 | Se você estiver compartilhando cartões com uma extensão de mensagem, faz sentido adicionar um pequeno link a uma página de saber mais para ajudar a apresentar aos usuários o que mais seu aplicativo pode fazer? |
| 3 | Você espera que a maioria das pessoas já tenha algum contexto sobre o objetivo do seu aplicativo ou que já tenha usado seus serviços em outro contexto? |
| 4 | Eles estão chegando ao seu aplicativo sem conhecimento prévio? |

</details>
<br>
<details>
<summary>Aplicativos do escopo pessoal</summary>

| # | Considere: |
| --- | --- |
| 1 | Existem interações individuais com o aplicativo necessárias por razões de privacidade ou outros? Por exemplo, verificar o saldo da licença ou outras informações privadas. |
| 2 | Eles serão uma colaboração entre usuários que podem não ter equipes comuns? Por exemplo, encontrar os próximos eventos em toda a organização em uma empresa. |
| 3 | Existem notificações ou mensagens personalizadas que precisam ser enviadas a um usuário em toda a experiência do aplicativo Teams? |

</details>
<br>
<details>
<summary>Aplicativos do escopo compartilhado</summary>

| # | Considere: |
| --- | --- |
| 1 | As informações apresentadas pelo aplicativo, seja na guia ou através de um bot, são relevantes e úteis para a maioria dos membros de uma Equipe? Por exemplo, o aplicativo Scrum. |
| 2 | O contexto do aplicativo pode mudar dependendo da equipe na qual ele é adicionado? Por exemplo, as tarefas do Planner são diferentes em equipes diferentes. |
| 3 | É possível que todos os membros de uma persona que precisam colaborar façam parte de uma única equipe? Por exemplo, os agentes que trabalham em um ticket. |

</details>
<br>
<details>
<summary>Escolha o ambiente da build</summary>

Com o Microsoft Teams, você pode escolher o ambiente de compilação que melhor se adapta aos seus requisitos de aplicativo. Use o Kit de Ferramentas do Teams ou outros SDKs, como C#, Blazor, Node.js e muito mais para começar. Para obter mais informações, confira [planejar seu aplicativo com recursos do Teams](../app-fundamentals-overview.md).

Sugestão: Opções que ajudam a selecionar o ambiente correto com base nas necessidades do aplicativo.
</details>
<br>
<details>
<summary>Planeje o teste do aplicativo</summary>

Depois de integrar seu aplicativo como o Microsoft Teams, teste-o antes de publicá-lo. O objetivo final é obter o máximo de usuários para seu aplicativo, portanto, certifique-se de testar o aplicativo em múltiplos dispositivos que os usuários poderiam usar. Para obter mais informações, confira [testar seu aplicativo](../build-and-test/test-app-overview.md).

Sugestão: Opções que ajudam a determinar o melhor ambiente de teste para o aplicativo.
</details>
<br>
<details>
<summary>Planejar a distribuição do aplicativo</summary>

Você pode fornecer seu aplicativo Microsoft Teams para um indivíduo, equipe, organização ou qualquer pessoa que queira usá-lo. A maneira como você distribui depende de vários fatores, incluindo necessidades dos usuários, requisitos técnicos e de negócios e suas metas para o aplicativo. Para obter mais informações, confira [distribuir seu aplicativo do Microsoft Teams](../deploy-and-publish/apps-publish-overview.md).

Sugestão: Opções que ajudam a determinar o melhor modelo de distribuição.

</details>

## <a name="plan-for-hosting-your-teams-app"></a>Planeje a hospedagem do seu aplicativo Teams

O Teams não hospeda seu aplicativo. Quando um usuário instala seu aplicativo no Teams, instala um pacote de aplicativo que contém apenas um arquivo de configuração (também conhecido como manifesto do aplicativo) e os ícones do aplicativo. A lógica e o armazenamento de dados do aplicativo são hospedados em outro lugar, como no localhost durante o desenvolvimento e nos Serviços Web do Azure. O Teams acessa esses recursos via HTTPS.

:::image type="content" source="../../assets/images/teams-app-host.png" alt-text="Ilustração mostrando a hospedagem de aplicativos para o aplicativo do Teams.":::

## <a name="plan-beyond-app-building"></a>Planeje além da criação de aplicativos

- **Decida o que acontece no Teams**: Seja um aplicativo novo ou um existente, verifique se deseja o aplicativo inteiro no cliente do Microsoft Teams. Se você integrar apenas uma parte do aplicativo, concentre-se no compartilhamento, colaboração, inicialização e monitoramento dos fluxos de trabalho.

- **Planeje a experiência de integração**: Crie sua experiência de integração com seus principais usuários em mente. A forma como você introduz um bot de chat instalado em um canal com mil pessoas é diferente quando instalado em um chat individual.

- **Planeje o futuro**: Identifique os novos recursos que o usuário preferirá na solução atual. Quaisquer novos recursos podem afetar o design e a arquitetura do aplicativo.
