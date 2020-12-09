---
title: Aplicativos nas reuniões do teams
author: laujan
description: Visão geral dos aplicativos nas reuniões do Microsoft Teams com base no participante e na função de usuário
ms.topic: overview
ms.author: lajanuar
keywords: API de função de participante do usuário de reuniões de aplicativos do teams
ms.openlocfilehash: 8a1b5b7d95e91273c794a2aa86a51e0ddeb1c610
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605155"
---
# <a name="apps-in-teams-meetings"></a>Aplicativos nas reuniões do teams

As reuniões são fundamentais para a produtividade no Microsoft Teams. Eles permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo. Como desenvolvedor, você pode criar uma [guia configurável](../tabs/what-are-tabs.md#how-do-tabs-work), [bot](../bots/what-are-bots.md)e aplicativos de [extensão de mensagem](../messaging-extensions/what-are-messaging-extensions.md) para aprimorar e enriquecer uma experiência de reunião do teams. Os usuários da reunião podem acessar os aplicativos, por meio da Galeria de guias, para habilitar os cenários relevantes, como preparar um quadro Kanban, iniciar uma caixa de diálogo acionável em reunião ou criar uma votação de reunião. O aplicativo de reunião pode fornecer uma experiência do usuário para cada estágio do ciclo de vida da reunião com base no status do participante.

Centros de extensibilidade de aplicativos da reunião da equipe em três conceitos:

✔ **Ciclo de vida da reunião** — antes, durante e após o período de reunião.  
✔ **Função participante** — organizador da reunião, apresentador ou participante.  
✔ **Tipo de usuário** , usuário no locatário, convidado, federado ou equipes anônimas.

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a>Cenários de ciclo de vida da reunião

## <a name="tabs"></a>Guias

> [!IMPORTANT]
> Assim como ocorre com todos os aplicativos de guia, seu aplicativo precisará seguir o [fluxo de autenticação SSO](../tabs/how-to/authentication/auth-aad-sso.md) do teams para guias.

> [!NOTE]
> Os clientes móveis dão suporte a guias apenas nas superfícies de reunião prévia e posterior. As experiências de reunião (painel e caixa de diálogo na reunião) no Mobile estarão disponíveis em breve

### <a name="pre-meeting-app-experience"></a>Experiência do aplicativo de pré-venda

**Experiência antes da reunião:**

![experiência de pré-venda](../assets/images/apps-in-meetings/PreMeeting.png)

**Guia antes da reunião:**

![exibição da guia pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ Usuários com permissão podem adicionar aplicativos a uma reunião por meio da Galeria de guias de duas maneiras:

&emsp;&emsp;&#9679; por meio da guia **detalhes** no formulário de agendamento do teams.

&emsp;&emsp;&#9679; por meio da guia **chat** de reunião em uma reunião existente.</br> </br>

✔ Os aplicativos de guia podem ser acessados em páginas de **detalhes** de reuniões e **chats** usando um botão de adição (➕). |

✔ O layout da guia deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.

### <a name="in-meeting-app-experience"></a>Experiência do aplicativo na reunião

✔ Os aplicativos de reunião serão hospedados na barra superior superior da janela de bate-papo e como experiência de guia na reunião através da guia na reunião. Quando os usuários adicionam uma guia a uma reunião através da Galeria de guias, os aplicativos que estão durante as experiências de **reunião** serão exibidos.

✔ Usuários com permissão podem adicionar aplicativos enquanto estiverem na reunião.

✔ Quando carregado no contexto de uma reunião, os aplicativos poderão aproveitar o SDK do cliente do teams para acessar o `meetingId` , `userMri` e `frameContext` para renderizar apropriadamente a experiência.

✔ Exportação de um resultado de uma pesquisa ou sondagens devem notificar os usuários, "resultados baixados com êxito".

✔ Para um aplicativo fique visível em uma reunião do teams em duas áreas:

&emsp;&emsp;**Painel lateral**&#9679;. </br>

> [!NOTE]
> Se o _manifesto do aplicativo_ especificar que a guia será [otimizada para o painel lateral](create-apps-for-teams-meetings.md#during-a-meeting), isso será exibido. Também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeita às diretrizes de design especificadas.

&emsp;&emsp;&#9679; **caixa de diálogo de reunião**. Use a caixa de diálogo de reunião para exibir conteúdo acionável para os participantes da reunião. *Consulte* [criar aplicativos para reuniões do teams](create-apps-for-teams-meetings.md).

**Experiência de reunião:**

![experiência na reunião](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Visão da caixa de diálogo no Meeting](../assets/images/apps-in-meetings/in-meeting-dialog.png)

**Caixa de diálogo acionável na reunião para usuários:**

![exibição da caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>Experiência do aplicativo após reunião

**Experiência de reunião:**

![Exibir reunião](../assets/images/apps-in-meetings/PostMeeting.png)

✔ Cenário de aplicativo após a reunião é semelhante à experiência de reunião atual com o benefício adicional de ter guias existentes na superfície. 

✔ Usuários com permissão podem adicionar aplicativos da Galeria de guias a uma reunião por meio da guia **detalhes** no formulário de agendamento de equipes e na guia **chat** de reunião em uma reunião existente.

✔ O layout da guia deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.

### <a name="bots"></a>Bots

Para implementação de bot, Confira nossos [bots na documentação de reuniões do Microsoft Teams](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) .

### <a name="messaging-extensions"></a>Extensões de Mensagens

Para implementação de extensão de mensagens, Confira nossa documentação [de mensagens de reuniões do teams](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) .

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Funções de participante e tipos de usuários em uma reunião

![Participantes de uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Funções de participante

Você pode criar seu aplicativo com autorização específica do participante. Por exemplo, talvez apenas um organizador e/ou apresentador possa criar uma pesquisa em reuniões. Embora as configurações de participante padrão sejam determinadas pelo administrador de ti de uma organização, um organizador da reunião pode querer alterar as configurações de uma reunião específica. Os organizadores podem fazer essas alterações na página da Web opções de reunião.

1. **Organizador**. O organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião. Somente os usuários com uma conta do M365 (que possui uma licença do Teams) podem ser organizadores e controlar as permissões dos participantes.
1. **Apresentador**. Os apresentadores têm praticamente os mesmos recursos do organizador; no entanto, um apresentador não pode remover um organizador da sessão ou modificar as opções de reunião da sessão. Por padrão, os participantes que ingressam em uma reunião têm a função apresentador.
1. **Participante**. Um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador. Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma configuração de reunião ou compartilhar conteúdo.

_Ver_ [ **funções em uma reunião do teams**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

Você pode acessar a página  **Opções de reunião** da seguinte maneira:

&#11200; no Microsoft Teams, **vá para** ![ o logotipo calendário calendário ](../assets/images/apps-in-meetings/calendar-logo.png) , selecione uma reunião e, em seguida, **Opções de reunião**.

&#11200; em um convite de reunião, selecione **Opções de reunião**.

&#11200; durante uma reunião, selecione **Mostrar participantes** ![ Mostrar ícone ](../assets/images/apps-in-meetings/show-participants.png) de participantes nos controles da reunião. Em seguida, acima da lista de participantes, escolha **gerenciar permissões**.

### <a name="user-types"></a>Tipos de usuários

> [!NOTE]
> Os tipos de usuário podem participar de reuniões e assumir uma das funções de participante descritas acima. O tipo de usuário não é exposto como parte da API **getParticipantRole** .

1. **Dentro do locatário**. Esses usuários pertencem à organização e têm credenciais no Azure Active Directory para o locatário. Em geral, eles são funcionários remotos ou no local.
1. **Convidado**. Um convidado é um participante de outra organização que tenha sido convidado a acessar o Microsoft Teams ou outros recursos no locatário da sua organização. Os convidados são adicionados ao Active Directory da sua organização e podem receber praticamente todos os mesmos recursos do teams que um membro da equipe nativo com acesso total aos bate-papos, reuniões e arquivos da equipe. _Ver_ [o acesso de convidados no Microsoft Teams](/microsoftteams/guest-access)
1. **Federado/externo**. Um usuário federado é um usuário do teams externo em outra organização que foi convidado a participar de uma reunião. Como esses usuários têm credenciais válidas com parceiros federados, eles são tratados como autenticados pelo Teams, mas não têm acesso às suas equipes ou a outros recursos compartilhados da sua organização. Se você deseja que usuários externos tenham acesso a equipes e canais, o acesso de convidados pode ser uma opção melhor. _Consulte_ [gerenciar o acesso externo no Microsoft Teams](/microsoftteams/manage-external-access)
1. **Anônimo**. Os usuários anônimos não têm uma identidade do Active Directory e não são federados com um locatário. O participante anônimo é como um usuário externo, mas sua identidade não é projetada na reunião. Usuários anônimos não poderão acessar aplicativos em uma janela de reunião.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Crie aplicativos para reuniões do Teams](create-apps-for-teams-meetings.md)
