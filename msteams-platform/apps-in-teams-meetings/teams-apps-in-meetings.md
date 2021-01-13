---
title: Aplicativos em reuniões do Teams
author: laujan
description: visão geral dos aplicativos em reuniões do Teams com base na função de participante e usuário
ms.topic: overview
ms.author: lajanuar
keywords: teams apps meetings user participant role api
ms.openlocfilehash: 217737cbbf73104d4d78cf817e6df0244229c53c
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797754"
---
# <a name="apps-in-teams-meetings"></a>Aplicativos em reuniões do Teams

As reuniões são fundamentais para a produtividade no Teams. Eles permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo. Como desenvolvedor, você pode criar [aplicativos](../tabs/what-are-tabs.md#how-do-tabs-work) [](../messaging-extensions/what-are-messaging-extensions.md) de guia configurável, [bot](../bots/what-are-bots.md)e extensão de mensagem para aprimorar e enriquecer uma experiência de reunião do Teams. Os usuários da reunião podem acessar aplicativos, por meio da galeria de guias, para habilitar cenários relevantes, como pré-preparação de um quadro kanban, lançamento de uma caixa de diálogo a actionable na reunião ou criação de uma votação pós-reunião. Seu aplicativo de reunião pode oferecer uma experiência de usuário para cada estágio do ciclo de vida da reunião com base no status do participante.

A extensibilidade do aplicativo de reunião do Teams é voltada para três conceitos:

✔ ciclo **de vida da** reunião — antes, durante e após o período da reunião.  
✔ **participante** — organizador da reunião, apresentador ou participante.  
✔ tipo **de usuário** — usuário do Teams no locatário, convidado, federado ou anônimo.

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a>Cenários de ciclo de vida de reunião

## <a name="tabs"></a>Guias

> [!IMPORTANT]
> Assim como em todos os aplicativos de guia, seu aplicativo precisará seguir o fluxo de autenticação [SSO](../tabs/how-to/authentication/auth-aad-sso.md) do Teams para guias.

> [!NOTE]
> Os clientes móveis só suportam Guias em Superfícies de Pré e Pós-Reunião. As experiências na reunião (caixa de diálogo e painel na reunião) em dispositivos móveis estarão disponíveis em breve

### <a name="pre-meeting-app-experience"></a>Experiência de aplicativo de pré-reunião

**Experiência de pré-reunião:**

![experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

**Guia Pré-reunião:**

![visualização da guia pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ usuários com permissão podem adicionar aplicativos a uma reunião por meio da galeria de guias de duas maneiras:

&emsp;&emsp;&#9679; por meio da **guia Detalhes** do formulário de agendamento do Teams.

&emsp;&emsp;&#9679; por meio da **guia Chat de** reunião em uma reunião existente.</br> </br>

✔ os aplicativos de guia  podem ser acessados em páginas de Detalhes e **Chats** de reuniões usando um botão de ícone de a ➕(|)

✔ layout da guia deve estar em um estado organizado se houver mais de dez votações ou pesquisas.

### <a name="in-meeting-app-experience"></a>Experiência do aplicativo na reunião

✔ aplicativos de reunião serão hospedados na barra superior da janela de chat e como experiência de guia na reunião por meio da guia na reunião. Quando os usuários adicionam uma guia a uma reunião por meio da galeria de guias, os aplicativos que estão **durante as experiências** de reunião serão divulgados.

✔ usuários com permissão podem adicionar aplicativos durante a reunião.

✔ Quando carregados no contexto de uma reunião, os aplicativos poderão aproveitar o SDK do Cliente do Teams para acessar o , e renderizar adequadamente a `meetingId` `userMri` `frameContext` experiência.

✔ exportar um resultado de uma pesquisa ou votações deve notificar os usuários informando, "resultados baixados com êxito".

✔ um aplicativo ficar visível em uma reunião do Teams em duas áreas:

&emsp;&emsp;&#9679; painel **lateral.** </br>

> [!NOTE]
> Se o _manifesto do_ aplicativo especifica que a guia é otimizada para o painel [lateral,](create-apps-for-teams-meetings.md#during-a-meeting)é onde ela será exibida. Ele também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeito às diretrizes de design especificadas.

&emsp;&emsp;&#9679; caixa **de diálogo na reunião.** Use a caixa de diálogo na reunião para demonstrar conteúdo a actionable para os participantes da reunião. *Confira* [Criar aplicativos para reuniões do Teams.](create-apps-for-teams-meetings.md)

**Experiência na reunião:**

![experiência na reunião](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Exibição de caixa de diálogo na reunião](../assets/images/apps-in-meetings/in-meeting-dialog.png)

**Caixa de diálogo a actionable na reunião para os usuários:**

![exibição de caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>Experiência de aplicativo pós-reunião

**Experiência pós-reunião:**

![post meeting view](../assets/images/apps-in-meetings/PostMeeting.png)

✔ O cenário de aplicativo pós-reunião é semelhante à experiência pós-reunião atual, com o benefício agregado de ter guias existentes na superfície. 

✔ Os usuários com permissão podem adicionar aplicativos da  galeria de guias a uma reunião por meio da guia Detalhes no formulário de agendamento do Teams e na guia **Chat** de reunião em uma reunião existente.

✔ layout da guia deve estar em um estado organizado se houver mais de dez votações ou pesquisas.

### <a name="bots"></a>Bots

Para implementação de bot, confira nossos [Bots na documentação de reuniões do Teams.](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings)

### <a name="messaging-extensions"></a>Extensões de Mensagens

Para a implementação da extensão de mensagens, confira nossas [extensões de mensagens na documentação de reuniões do Teams.](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings)

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Funções de participante e tipos de usuário em uma reunião

![Participantes em uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Funções de participante

Você pode projetar seu aplicativo com autorização específica do participante. Por exemplo, talvez apenas um organizador e/ou apresentador possam criar uma votação em reuniões. Embora as configurações de participantes padrão sejam determinadas pelo administrador de IT de uma organização, um organizador da reunião pode querer alterar as configurações de uma reunião específica. Os organizadores podem fazer essas alterações na página da Web de opções de reunião.

1. **Organizador**. O organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião. Somente os usuários com uma conta do M365 (que possuem uma licença do Teams) podem ser organizadores e controlar as permissões dos participantes.
1. **Apresentador.** Os apresentadores têm quase os mesmos recursos que o organizador; no entanto, um apresentador não pode remover um organizador da sessão ou modificar as opções de reunião da sessão. Por padrão, os participantes que participam de uma reunião têm a função de apresentador.
1. **Attendee**. Um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador. Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar as configurações da reunião ou compartilhar conteúdo.

_Ver_ [ **Funções em uma reunião do Teams**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

Você pode acessar a  **página de opções de** reunião da seguinte forma:

&#11200; Teams, vá para **o** logotipo do ![ ](../assets/images/apps-in-meetings/calendar-logo.png) calendário, selecione uma reunião e, em seguida, opções **de reunião.**

&#11200; Em um convite de reunião, selecione opções **de reunião.**

&#11200; Durante uma reunião, selecione **Mostrar** participantes que mostram o ![ ícone dos participantes nos ](../assets/images/apps-in-meetings/show-participants.png) controles da reunião. Em seguida, acima da lista de participantes, escolha **Gerenciar permissões.**

### <a name="user-types"></a>Tipos de usuários

> [!NOTE]
> Os tipos de usuário podem ingressar em reuniões e assumir uma das funções de participante descritas acima. O tipo de usuário não é exposto como parte da API **getParticipantRole.**

1. **No locatário.** Esses usuários pertencem à organização e têm credenciais no Azure Active Directory para o locatário. Geralmente, eles são funcionários em tempo integral, no local ou remotos.
1. **Convidado**. Um convidado é um participante de outra organização que foi convidado a acessar o Teams ou outros recursos no locatário da sua organização. Os convidados são adicionados ao Active Directory da sua organização e podem receber quase todos os mesmos recursos do Teams de um membro nativo da equipe com acesso total a chats, reuniões e arquivos da equipe. _Ver_ [acesso de convidados no Microsoft Teams](/microsoftteams/guest-access)
1. **Federado/Externo**. Um usuário federado é um usuário externo do Teams em outra organização que foi convidado a ingressar em uma reunião. Como esses usuários têm credenciais válidas com parceiros federados, eles são tratados como autenticados pelo Teams, mas não têm acesso às suas equipes ou outros recursos compartilhados da sua organização. Se você quiser que usuários externos tenham acesso a equipes e canais, o acesso de convidados pode ser uma opção melhor. _Confira_ [Gerenciar o acesso externo no Microsoft Teams](/microsoftteams/manage-external-access)
1. **Anônimo**. Os usuários anônimos não têm uma identidade do Active Directory e não são federados com um locatário. O participante anônimo é como um usuário externo, mas sua identidade não é projetada para a reunião. Os usuários anônimos não poderão acessar aplicativos em uma janela de reunião.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar seu aplicativo](create-apps-for-teams-meetings.md)
> [!div class="nextstepaction"]
> [Criar seu aplicativo](create-apps-for-teams-meetings.md)
