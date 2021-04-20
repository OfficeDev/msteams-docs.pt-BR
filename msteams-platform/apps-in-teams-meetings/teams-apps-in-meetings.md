---
title: Aplicativos em reuniões do Teams
author: laujan
description: visão geral dos aplicativos em reuniões do Teams com base na função de usuário e participante
ms.topic: overview
ms.author: lajanuar
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: 201fa58cc375440cf6c495028135e32fd51f740c
ms.sourcegitcommit: ee8c4800da3b3569d80c6f3661a2f20aa1f2c5e2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2021
ms.locfileid: "51885077"
---
# <a name="apps-in-teams-meetings"></a>Aplicativos em reuniões do Teams

As reuniões permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo. O aplicativo de reunião pode oferecer uma experiência do usuário para cada estágio do ciclo de vida da reunião, incluindo a experiência do aplicativo pré-reunião, na reunião e pós-reunião, dependendo do status do participante.

Os usuários finais do Teams podem acessar aplicativos durante reuniões usando a galeria de guias, por exemplo:

* Pré-estágio de um quadro Kanban
* Iniciar uma caixa de diálogo acionável na reunião
* Criar uma sondagem pós-reunião

A extensibilidade do aplicativo de reunião do Teams baseia-se nos seguintes conceitos:

✔ ciclo de vida da reunião tem estágios como antes, durante e após o período de tempo de reunião.  
✔ Funções de participante em uma reunião, como organizador da reunião, apresentador ou participante.  
✔ Tipos de usuário em uma reunião, como no locatário, convidado, federado ou usuário anônimo do Teams.

Este artigo aborda informações sobre o ciclo de vida da reunião e como integrar guias, bots e extensões de mensagens em sua reunião. Ele também permite identificar funções de participantes e também usar diferentes tipos de usuário para executar tarefas.

> [!NOTE]
> Para trabalhar com os recursos de extensibilidade do aplicativo de reunião, você deve ter as permissões apropriadas.

### <a name="meeting-lifecycle"></a>Ciclo de vida da reunião

O ciclo de vida da reunião consiste na experiência do aplicativo de pré-reunião, na reunião e pós-reunião. Você pode integrar guias, bots e extensões de mensagens em cada estágio do ciclo de vida da reunião.

## <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrar guias ao ciclo de vida da reunião

As guias permitem que os membros da equipe acessem serviços e conteúdo em um espaço específico em um canal ou chat. Isso permite que a equipe trabalhe diretamente com guias e tenha conversas sobre as ferramentas e dados disponíveis nas guias. Na reunião do Teams, os usuários podem adicionar uma guia selecionando mais <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>e escolher o aplicativo que eles querem instalar como uma guia.

> [!IMPORTANT]
> Se você tiver integrado uma guia à sua reunião, seu aplicativo deverá seguir o fluxo de autenticação de logom único [(SSO)](../tabs/how-to/authentication/auth-aad-sso.md) do Teams para guias.

> [!NOTE]
> * Os clientes móveis suportam guias somente em estágios pré e pós-reunião. As experiências em reunião que estão na caixa de diálogo e no painel da reunião não estão disponíveis no momento em dispositivos móveis.
> * Os aplicativos têm suporte apenas em reuniões agendadas privadas.

### <a name="pre-meeting-app-experience"></a>Experiência do aplicativo de pré-reunião

**Experiência de pré-reunião:**

![experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

**Guia Pré-reunião:**

![exibição de guia de pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ usuários com permissão são usuários que podem adicionar aplicativos a uma reunião durante diferentes estágios do ciclo de vida da reunião. Esses usuários podem adicionar aplicativos a uma reunião por meio da galeria de guias de duas maneiras:

   * Usando a **guia Detalhes** no formulário de agendamento do Teams.

   * Usando a guia **Chat de** reunião em uma reunião existente.

✔ aplicativos tab são acessíveis em reuniões **Páginas detalhes** e **chats** usando um botão de ➕ de adoção.

✔ layout tab deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.

### <a name="in-meeting-app-experience"></a>Experiência do aplicativo na reunião

✔ aplicativos de reunião são hospedados na barra superior superior da janela de chat e como experiência de guia na reunião usando a guia na reunião. Quando os usuários adicionam uma guia a uma reunião por meio da galeria de guias, os aplicativos que são **durante as experiências de** reunião são mostrados.

✔ usuários com permissão podem adicionar aplicativos durante a reunião.

✔ Quando carregado no contexto de uma reunião, os aplicativos podem aproveitar o SDK do cliente do Teams para acessar o , e renderizar adequadamente `meetingId` `userMri` a `frameContext` experiência.

✔ Exportar um resultado de uma pesquisa ou sondagem notifica os usuários que os resultados foram baixados com êxito.

✔ Um aplicativo fica visível em uma reunião do Teams no painel lateral ou na caixa de diálogo na reunião. Use a caixa de diálogo na reunião para mostrar conteúdo a actionable para os participantes da reunião. Para obter mais informações, consulte [create apps for Teams meetings](create-apps-for-teams-meetings.md).

   > [!NOTE]
   > O manifesto do aplicativo especifica que sua guia é [otimizada](create-apps-for-teams-meetings.md#during-a-meeting)para o painel lateral , que é onde ele é exibido. Ele também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeito a diretrizes de design especificadas.

As imagens a seguir exibem o aplicativo como uma caixa de diálogo na reunião e como um painel lateral separado:

![Experiência na reunião](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Exibição de diálogo na reunião](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="in-meeting-actionable-dialog-for-users"></a>Caixa de diálogo a actionable na reunião para usuários

![Exibição de caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>Experiência de aplicativo pós-reunião

![Exibição pós-reunião](../assets/images/apps-in-meetings/PostMeeting.png)

✔ O cenário do aplicativo pós-reunião é semelhante à experiência atual pós-reunião com o benefício adicionado de ter guias que existem dentro da superfície.

✔ os usuários com permissão podem adicionar aplicativos da  galeria de guias a uma reunião usando a guia Detalhes no formulário de agendamento do Teams e a guia **Chat** de reunião em uma reunião existente.

✔ layout da guia deve ser organizado quando houver mais de dez pesquisas ou pesquisas.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrar bots ao ciclo de vida da reunião

Para implementação de bot, comece com [a complicação de um bot](../build-your-first-app/build-bot.md) e continue com a criação de [aplicativos para reuniões do Teams.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrar extensões de mensagens ao ciclo de vida da reunião

Para implementação de extensão de mensagens, comece com [a criação](../messaging-extensions/how-to/create-messaging-extension.md) de uma extensão de mensagens e continue com a criação de [aplicativos para reuniões do Teams.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Funções de participante e tipos de usuário em uma reunião

![Participantes de uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Funções de participante

As configurações de participante padrão são determinadas pelo administrador de IT de uma organização. Veja a seguir as funções dos participantes em uma reunião:

* **Organizador**: o organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião. Somente usuários com uma conta M365 com uma licença do Teams podem ser organizadores e controlar as permissões do participante. Um organizador da reunião pode alterar as configurações de uma reunião específica. Os organizadores podem fazer essas alterações na página da Web **opções de** reunião.
* **Apresentador :** os apresentadores têm os mesmos recursos que o organizador. No entanto, um apresentador não pode remover um organizador da sessão ou modificar opções de reunião para a sessão. Por padrão, os participantes que participam de uma reunião têm a função de apresentador.
* **Participante**: um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador. Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma das configurações de reunião ou compartilhar conteúdo.

Somente um organizador ou apresentador pode adicionar, remover ou desinstalar aplicativos. Somente organizador ou apresentador pode criar votações em uma reunião.

Para obter mais informações, [consulte funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Você pode acessar a página  **Opções de reunião** da seguinte forma:

* No Teams, vá **para** o logotipo do ![ ](../assets/images/apps-in-meetings/calendar-logo.png) calendário, selecione uma reunião e, em seguida, **opções de reunião.**

* Em um convite de reunião, selecione **Opções de reunião**.

* Durante uma reunião, selecione **Mostrar que os participantes** mostram o ícone dos participantes nos ![ ](../assets/images/apps-in-meetings/show-participants.png) controles de reunião. Em seguida, acima da lista de participantes, escolha **Gerenciar permissões**.

### <a name="user-types"></a>Tipos de usuários

> [!NOTE]
> Os usuários com tipos de usuário específicos atribuídos a eles podem participar de reuniões e assumir uma das funções de participante descritas nas [funções de participante.](#participant-roles) O tipo de usuário não está incluído na API **getParticipantRole.**

Os seguintes tipos de usuário identificam o que cada usuário pode fazer e o que podem acessar:

* **In-tenant**: Os usuários no locatário pertencem à organização e têm credenciais no Azure Active Directory (AAD) para o locatário. Eles geralmente são funcionários em tempo integral, no local ou remotos. Um usuário no locatário pode ser um organizador, apresentador ou participante.
* **Convidado**: um convidado é um participante de outra organização convidado para acessar o Teams ou outros recursos no locatário da organização. Os convidados são adicionados ao AAD da sua organização e têm os mesmos recursos do Teams como um membro nativo da equipe com acesso a chats, reuniões e arquivos de equipe. Um usuário convidado pode ser organizador, apresentador ou participante. Para obter mais informações, consulte [acesso de convidados no Teams](/microsoftteams/guest-access).
* **Federado ou externo**: um usuário federado é um usuário externo do Teams em outra organização que foi convidado a participar de uma reunião. Esses usuários têm credenciais válidas com parceiros federados e são autorizados pelo Teams. Eles não têm acesso às suas equipes ou a outros recursos compartilhados da sua organização. O acesso de convidados é uma opção melhor para usuários externos ter acesso a equipes e canais. Para obter mais informações, consulte [manage external access in Teams](/microsoftteams/manage-external-access).
* **Anônimo**: os usuários anônimos não têm uma identidade AAD e não são federados com um locatário. O participante anônimo é como um usuário externo, mas sua identidade não é projetada na reunião. Um usuário anônimo não pode ser um organizador, mas pode ser um apresentador ou um participante.

> [!NOTE]
> Os usuários anônimos herdam a política de permissão de aplicativo padrão global no nível do usuário. Para obter mais informações, consulte [Manage Apps](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

A tabela a seguir fornece os tipos de usuário e quais recursos cada usuário pode acessar:

| Tipo de usuário | Guias | Bots | Extensões de mensagens | Cartões Adaptáveis | Módulos de tarefas | Caixa de diálogo na reunião |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Usuário anônimo | Não disponível | Não disponível | Não disponível | Interações no chat de reunião são permitidas. | Interações no chat de reunião de um Cartão Adaptável são permitidas. | Não disponível |
| Convidado que faz parte do locatário AAD | A interação é permitida. Não é permitido criar, atualizar e excluir. | Não disponível | Não disponível | Interações no chat de reunião são permitidas. | Interações no chat de reunião de um Cartão Adaptável são permitidas. | Disponível |
| Federado | Não disponível | Não disponível | Não disponível | Não disponível | Não disponível | Não disponível |

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Tab](../tabs/what-are-tabs.md#how-do-tabs-work)

> [!div class="nextstepaction"]
> [Bot](../bots/what-are-bots.md)

> [!div class="nextstepaction"]
> [Extensão de mensagem](../messaging-extensions/what-are-messaging-extensions.md)

> [!div class="nextstepaction"]
> [Criar seu aplicativo](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar seu aplicativo](create-apps-for-teams-meetings.md)
