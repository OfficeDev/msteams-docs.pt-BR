---
title: Perguntas para ajudar a planejar o desenvolvimento de aplicativos do Microsoft Teams
author: heath-hamilton
description: Perguntas a serem consideradas enquanto você planeja seu aplicativo, entende seu usuário e suas necessidades, entende os problemas do usuário que seu aplicativo resolveria, planeja a autenticação do usuário e sua experiência de integração
ms.topic: conceptual
ms.localizationpriority: high
ms.author: surbhigupta
ms.openlocfilehash: b0d9450f3d729131b28dbf744843eeeda1b91c22
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756748"
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

| # | Considere: |
| --- | --- |
| 1 | Os usuários são principalmente trabalhadores da linha de frente em clientes móveis? |
| 2 | Você espera que muitos usuários convidados precisem de acesso ao aplicativo? |
| 3 | Eles usam equipes e canais ou principalmente chats em grupo? |
| 4 | Quão tecnicamente sofisticados são seus principais usuários? |
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

| # | Considere:|
|--- | --- |
| 1 | Os usuários acessarão diferentes visualizações de dados com base nas suas funções? |
| 2 | Existem dados pessoais envolvidos? |
| 3 | As interações também serão baseadas nas funções do usuário? |
| 4 | Usuários externos acessarão o aplicativo? |

</details>
<br>
<details>
<summary>Planeje a experiência de integração</summary>

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

Sugestão: Opções que ajudam a selecionar o ambiente correto com base nas necessidades do aplicativo.
</details>
<br>
<details>
<summary>Planeje o teste do aplicativo</summary>

Sugestão: Opções que ajudam a determinar o melhor ambiente de teste para o aplicativo.
</details>
<br>
<details>
<summary>Planejar a distribuição do aplicativo</summary>

Sugestão: Opções que ajudam a determinar o melhor modelo de distribuição.

</details>

## <a name="plan-for-hosting-your-teams-app"></a>Planeje a hospedagem do seu aplicativo Teams

O Teams não hospeda seu aplicativo. Quando um usuário instala seu aplicativo no Teams, ele instala um pacote de aplicativo que contém um único arquivo de configuração (também conhecido como manifesto do aplicativo) e os ícones do aplicativo. A lógica e o armazenamento de dados do aplicativo são hospedados em outro lugar, como no localhost durante o desenvolvimento e nos Serviços Web do Azure. O Teams acessa esses recursos via HTTPS.

:::image type="content" source="../../assets/images/teams-app-host.png" alt-text="Ilustração mostrando a hospedagem de aplicativos para aplicativos do Teams" border="true":::

## <a name="plan-beyond-app-building"></a>Planeje além da criação de aplicativos

- **Decida o que acontece no Teams**: Seja um aplicativo novo ou um existente, verifique se deseja o aplicativo inteiro no cliente do Microsoft Teams. Se você integrar apenas uma parte do aplicativo, concentre-se no compartilhamento, colaboração, inicialização e monitoramento dos fluxos de trabalho.

- **Planeje a experiência de integração**: Crie sua experiência de integração com seus principais usuários em mente. A forma como você introduz um bot de chat instalado em um canal com mil pessoas é diferente quando instalado em um chat individual.

- **Planeje o futuro**: Identifique os novos recursos que o usuário preferirá na solução atual. Quaisquer novos recursos podem afetar o design e a arquitetura do aplicativo.
