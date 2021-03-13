---
title: Aplicativos em reuniões do Teams
author: laujan
description: visão geral dos aplicativos em reuniões do Teams com base na função de usuário e participante
ms.topic: overview
ms.author: lajanuar
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: 51fe2e0ebdaa56197bbebd1e5dbcf90698fb1f92
ms.sourcegitcommit: 23ed7edf145df10dcfba15c43978eae9e0d451a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2021
ms.locfileid: "50753550"
---
# <a name="apps-in-teams-meetings"></a>Aplicativos em reuniões do Teams

As reuniões são fundamentais para a produtividade no Teams. Eles permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo. Como desenvolvedor, você pode criar aplicativos [de guia,](../tabs/what-are-tabs.md#how-do-tabs-work) [bot](../bots/what-are-bots.md)e extensão de [mensagem](../messaging-extensions/what-are-messaging-extensions.md) configuráveis para aprimorar e enriquecer uma experiência de reunião do Teams. Os usuários da reunião podem acessar aplicativos, por meio da galeria de guias, para habilitar cenários relevantes, como pré-preparação de um quadro Kanban, iniciar uma caixa de diálogo ativas na reunião ou criar uma sondagem pós-reunião. Seu aplicativo de reunião pode oferecer uma experiência do usuário para cada estágio do ciclo de vida da reunião com base no status do participante.

Centros de extensibilidade do aplicativo de reunião do Teams em três conceitos:

✔ ciclo **de** vida da reunião — antes, durante e após o período de tempo de reunião.  
✔ Função **participante** — organizador da reunião, apresentador ou participante.  
✔ Tipo **de usuário** — no locatário, convidado, federado ou usuário anônimo do Teams.

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a>Cenários de ciclo de vida de reunião

## <a name="tabs"></a>Guias

> [!IMPORTANT]
> Assim como em todos os aplicativos de tabulação, seu aplicativo precisará seguir o fluxo de autenticação [SSO](../tabs/how-to/authentication/auth-aad-sso.md) do Teams para guias.

> [!NOTE]
> * Os clientes móveis suportam guias somente em superfícies de pré-reunião e pós-reunião. As experiências na reunião, como a caixa de diálogo na reunião e o painel no celular estarão disponíveis em breve.
> * Os aplicativos têm suporte apenas em reuniões agendadas privadas.

### <a name="pre-meeting-app-experience"></a>Experiência do aplicativo de pré-reunião

**Experiência de pré-reunião:**

![experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

**Guia Pré-reunião:**

![exibição de guia de pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ usuários com permissão podem adicionar aplicativos a uma reunião por meio da galeria de guias de duas maneiras:

&emsp;&emsp;&#9679; por meio da guia **Detalhes** no formulário de agendamento do Teams.

&emsp;&emsp;&#9679; por meio da guia **Chat de** reunião em uma reunião existente.</br> </br>

✔ aplicativos tab são acessíveis em reuniões **Páginas detalhes** e **chats** usando um botão de ícone de a mais (➕) .|

✔ layout da guia deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.

### <a name="in-meeting-app-experience"></a>Experiência do aplicativo na reunião

✔ aplicativos de reunião serão hospedados na barra superior superior da janela de chat e como experiência de guia na reunião por meio da guia na reunião. Quando os usuários adicionam uma guia a uma reunião por meio da galeria de guias, os aplicativos que estão **durante** as experiências de reunião serão ativos.

✔ usuários com permissão podem adicionar aplicativos durante a reunião.

✔ Quando carregado no contexto de uma reunião, os aplicativos poderão aproveitar o SDK do Cliente do Teams para acessar o , e renderizar adequadamente `meetingId` `userMri` a `frameContext` experiência.

✔ Exportar um resultado de uma pesquisa ou sondagens deve notificar os usuários informando, "resultados baixados com êxito".

✔ para que um aplicativo seja visível em uma reunião do Teams em duas áreas:

&emsp;&emsp;&#9679; Painel **lateral**. </br>

> [!NOTE]
> Se o _manifesto do aplicativo_ especificar que sua guia é otimizada para o painel [lateral,](create-apps-for-teams-meetings.md#during-a-meeting)é onde ela será exibida. Ele também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeito a diretrizes de design especificadas.

&emsp;&emsp;&#9679; caixa **de diálogo na reunião**. Use a caixa de diálogo na reunião para mostrar conteúdo a actionable para os participantes da reunião. *Consulte* [Criar aplicativos para reuniões do Teams.](create-apps-for-teams-meetings.md)

**Experiência na reunião:**

![experiência na reunião](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Exibição de diálogo na reunião](../assets/images/apps-in-meetings/in-meeting-dialog.png)

**Caixa de diálogo a actionable na reunião para usuários:**

![exibição de caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>Experiência de aplicativo pós-reunião

**Experiência pós-reunião:**

![pós-exibição de reunião](../assets/images/apps-in-meetings/PostMeeting.png)

✔ O cenário do aplicativo pós-reunião é semelhante à experiência atual pós-reunião com o benefício adicionado de ter guias que existem dentro da superfície. 

✔ usuários com permissão podem adicionar aplicativos da galeria  de guias a uma reunião por meio da guia Detalhes no formulário de agendamento do Teams e na guia **Chat** de reunião em uma reunião existente.

✔ layout da guia deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.

### <a name="bots"></a>Bots

Para implementação de bot, comece com [a complicação de um bot](../build-your-first-app/build-bot.md) e continue com a criação de [aplicativos para reuniões do Teams.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)

### <a name="messaging-extensions"></a>Extensões de mensagens

Para implementação de extensão de mensagens, comece com [a criação](../messaging-extensions/how-to/create-messaging-extension.md) de uma extensão de mensagens e continue com a criação de [aplicativos para reuniões do Teams.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Funções de participante e tipos de usuário em uma reunião

![Participantes de uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Funções de participante

Você pode projetar seu aplicativo com autorização específica do participante. Por exemplo, talvez apenas um organizador e/ou apresentador possam criar uma sondagem em reuniões. Embora as configurações de participantes padrão sejam determinadas pelo administrador de IT de uma organização, um organizador da reunião pode querer alterar as configurações de uma reunião específica. Os organizadores podem fazer essas alterações na página da Web opções de reunião.

1. **Organizador**. O organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião. Somente usuários com uma conta M365 (que possuem uma licença do Teams) podem ser organizadores e controlar as permissões do participante.
1. **Apresentador**. Os apresentadores têm quase os mesmos recursos que o organizador; no entanto, um apresentador não pode remover um organizador da sessão ou modificar opções de reunião para a sessão. Por padrão, os participantes que participam de uma reunião têm a função de apresentador.
1. **Participante**. Um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador. Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma das configurações de reunião ou compartilhar conteúdo.

_Consulte_ [ **Funções em uma reunião do Teams**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

Você pode acessar a página  **Opções de reunião** da seguinte forma:

&#11200; No Teams, vá  para o logotipo do ![ ](../assets/images/apps-in-meetings/calendar-logo.png) calendário, selecione uma reunião e opções **de reunião.**

&#11200; Em um convite de reunião, selecione **Opções de reunião**.

&#11200; Durante uma reunião, selecione **Mostrar que os** participantes mostram o ícone dos participantes nos ![ ](../assets/images/apps-in-meetings/show-participants.png) controles de reunião. Em seguida, acima da lista de participantes, escolha **Gerenciar permissões**.

### <a name="user-types"></a>Tipos de usuários

> [!NOTE]
> Os tipos de usuário podem ingressar em reuniões e assumir uma das funções de participante descritas acima. O tipo de usuário não é exposto como parte da API **getParticipantRole.**

1. **In-tenant**. Esses usuários pertencem à organização e têm credenciais no Azure Active Directory para o locatário. Eles geralmente são funcionários em tempo integral, no local ou remotos.
1. **Convidado**. Um convidado é um participante de outra organização que foi convidado a acessar o Teams ou outros recursos no locatário da sua organização. Os convidados são adicionados ao Active Directory da sua organização e podem receber quase todos os mesmos recursos do Teams como um membro nativo da equipe com acesso total a chats, reuniões e arquivos de equipe. _Consulte_ [Acesso de convidados no Microsoft Teams](/microsoftteams/guest-access)
1. **Federado/Externo**. Um usuário federado é um usuário externo do Teams em outra organização que foi convidado a participar de uma reunião. Como esses usuários têm credenciais válidas com parceiros federados, eles são tratados como autenticados pelo Teams, mas não têm acesso às suas equipes ou a outros recursos compartilhados de sua organização. Se você quiser que os usuários externos tenham acesso a equipes e canais, o acesso de convidados pode ser uma opção melhor. _Consulte_ [Gerenciar acesso externo no Microsoft Teams](/microsoftteams/manage-external-access)
1. **Anônimo**. Os usuários anônimos não têm uma identidade do Active Directory e não são federados com um locatário. O participante anônimo é como um usuário externo, mas sua identidade não é projetada para a reunião. Os usuários anônimos não poderão acessar aplicativos em uma janela de reunião.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar seu aplicativo](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
> [!div class="nextstepaction"]
> [Criar seu aplicativo](create-apps-for-teams-meetings.md)
