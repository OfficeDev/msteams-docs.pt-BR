---
title: Aplicativos em reuniões Teams
author: laujan
description: visão geral dos aplicativos em reuniões Teams com base na função de participante e usuário
ms.topic: overview
ms.author: lajanuar
localization_priority: Normal
keywords: equipes aplicativos reuniões usuário participante papel api
ms.openlocfilehash: c5419565d8defd03a3dcfcc5b05b9517cb4269e2
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565918"
---
# <a name="apps-in-teams-meetings"></a>Aplicativos em reuniões Teams

Os encontros permitem colaboração, parceria, comunicação informada e feedback compartilhado em um fórum inclusivo e ativo. O aplicativo de reunião pode oferecer uma experiência ao usuário para cada etapa do ciclo de vida do encontro, incluindo experiência de aplicativo pré-reunião, reunião e pós-reunião, dependendo do status do participante.

Teams usuários finais podem acessar aplicativos durante reuniões usando a galeria de guias, por exemplo:

* Pré-estágio de uma placa Kanban
* Inicie um diálogo acionável em reunião
* Crie uma enquete pós-reunião

Teams' reunião extensibilidade do aplicativo é baseada nos seguintes conceitos:

✔ O ciclo de vida do Encontro tem estágios como antes, durante e depois do período de tempo de encontro.  
✔ funções participantes em uma reunião como organizador de reuniões, apresentador ou participante.  
✔ Usuário em uma reunião como usuário de Teams inquilina, convidado, federado ou anônimo.

Este artigo abrange informações sobre o ciclo de vida do encontro e como integrar guias, bots e extensões de mensagens em sua reunião. Ele também permite identificar funções de participante e também usar diferentes tipos de usuários para executar tarefas.

> [!NOTE]
> Para trabalhar com os recursos de extensibilidade do aplicativo de reunião, você deve ter as permissões apropriadas.

### <a name="meeting-lifecycle"></a>Cumprindo o ciclo de vida

O ciclo de vida do encontro consiste em experiência de aplicativo pré-reunião, presencial e pós-reunião. Você pode integrar guias, bots e extensões de mensagens em cada etapa do ciclo de vida do encontro.

## <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrar guias no ciclo de vida do encontro

As guias permitem que os membros da equipe acessem serviços e conteúdos em um espaço específico dentro de um canal ou chat. Isso permite que a equipe trabalhe diretamente com guias e tenha conversas sobre as ferramentas e dados disponíveis nas guias. Em Teams reunião, os usuários podem adicionar uma guia selecionando mais <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>e escolher o aplicativo que eles querem instalar como uma guia.

> [!IMPORTANT]
> Se você tiver integrado uma guia com sua reunião, então seu aplicativo deve seguir o fluxo de autenticação Teams [único login (SSO)](../tabs/how-to/authentication/auth-aad-sso.md) para guias.

> [!NOTE]
> * Os clientes móveis suportam guias apenas em etapas pré e pós-reunião. As experiências de encontro que estão em diálogo e painel não estão disponíveis no celular.
> * Os aplicativos são suportados apenas em reuniões agendadas privadas.

### <a name="pre-meeting-app-experience"></a>Experiência de aplicativo pré-reunião

**Experiência pré-reunião:**

![experiência pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

**Guia de pré-reunião:**

![visualização de guia pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ usuários autorizados são usuários que podem adicionar aplicativos a uma reunião durante diferentes etapas do ciclo de vida do encontro. Esses usuários podem adicionar aplicativos a uma reunião através da galeria de guias de duas maneiras:

   * Usando a guia **Detalhes** no formulário de agendamento Teams.

   * Usando a guia **Chat de** reunião em uma reunião existente.

✔ aplicativos tab são acessíveis em reuniões **Detalhes** e páginas **de Bate-papos** usando um botão plus ➕.

✔ layout tab deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.

### <a name="in-meeting-app-experience"></a>Experiência de aplicativo no encontro

✔ Os aplicativos de reunião estão hospedados na barra superior superior da janela de bate-papo e como experiência de guia de reunião usando a guia de reunião. Quando os usuários adicionam uma guia a uma reunião através da galeria de guias, aplicativos que são durante as experiências **de reunião** são mostrados.

✔ os usuários autorizados podem adicionar aplicativos durante a reunião.

✔ Quando carregados no contexto de uma reunião, os aplicativos podem aproveitar o Teams cliente SDK para acessar o `meetingId` , e para tornar a experiência `userMri` `frameContext` adequadamente.

✔ Exportar resultado de uma pesquisa ou enquete notifica os usuários que os resultados baixaram com sucesso.

✔ Um aplicativo é visível em uma reunião Teams no painel lateral ou na caixa de diálogo em reunião. Use a caixa de diálogo em reunião para mostrar conteúdo acionável para os participantes do encontro. Para obter mais informações, consulte [criar aplicativos para reuniões Teams](create-apps-for-teams-meetings.md).

   > [!NOTE]
   > O manifesto do aplicativo especifica que sua guia é [otimizada para painel lateral,](create-apps-for-teams-meetings.md#during-a-meeting)que é onde é exibida. Também pode fazer parte de uma experiência de bandeja compartilhada, sujeita a diretrizes de design especificadas.

As imagens a seguir exibem o aplicativo como uma caixa de diálogo em reunião e como um painel lateral separado:

![Experiência de encontro](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Visão de diálogo em reunião](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="in-meeting-actionable-dialog-for-users"></a>Diálogo acionável em reunião para usuários

![Exibição de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>Experiência de aplicativo pós-reunião

![Visão de reunião pós](../assets/images/apps-in-meetings/PostMeeting.png)

✔ O cenário do aplicativo pós-reunião é semelhante à experiência atual pós-reunião com o benefício adicional de ter guias que existem dentro da superfície.

✔ os usuários autorizados podem adicionar aplicativos da galeria de guias a uma reunião usando a guia **Detalhes** no formulário de agendamento de Teams e na guia **Chat** de reunião em uma reunião existente.

✔ layout do Tab deve ser organizado quando houver mais de dez pesquisas ou pesquisas.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integre bots no ciclo de vida do encontro

Para implementação de bots, comece com [a construção de um bot](../build-your-first-app/build-bot.md) e, em seguida, continue com criar aplicativos para [reuniões Teams](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrar extensões de mensagens no ciclo de vida do encontro

Para implementação de extensão de mensagens, comece com [a construção de uma extensão de mensagens](../messaging-extensions/how-to/create-messaging-extension.md) e, em seguida, continue com criar aplicativos para [reuniões Teams](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Funções dos participantes e tipos de usuários em uma reunião

![Participantes de uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Funções participantes

As configurações padrão do participante são determinadas pelo administrador de TI de uma organização. A seguir, os papéis participantes em uma reunião:

* **Organizador**: O organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião. Somente usuários com uma conta M365 com uma licença de Teams podem ser organizadores e controlar as permissões dos participantes. Um organizador de reuniões pode alterar as configurações para uma reunião específica. Os organizadores podem fazer essas alterações na página da web de **opções do Encontro.**
* **Apresentador**: Os apresentadores têm as mesmas capacidades do organizador. No entanto, um apresentador não pode remover um organizador da sessão ou modificar opções de reunião para a sessão. Por padrão, os participantes que participam de uma reunião têm o papel de apresentador.
* **Participante**: Um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador. Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma das configurações da reunião ou compartilhar conteúdo.

Apenas um organizador ou apresentador pode adicionar, remover ou desinstalar aplicativos. Apenas o organizador ou apresentador pode criar pesquisas em uma reunião.

Para obter mais informações, consulte [papéis em uma reunião Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Você pode acessar a página  **de opções de Reunião** da seguinte forma:

* Em Teams, acesse o logotipo do calendário **do** ![ ](../assets/images/apps-in-meetings/calendar-logo.png) Calendário, selecione uma reunião e, em seguida, **as opções de reunião**.

* Em um convite de reunião, selecione **Opções de reunião.**

* Durante uma reunião, selecione **Mostrar aos participantes** ![ o ícone nos controles de ](../assets/images/apps-in-meetings/show-participants.png) reunião. Em seguida, acima da lista de participantes, escolha **Gerenciar permissões**.

### <a name="user-types"></a>Tipos de usuários

> [!NOTE]
> Usuários com tipos de usuários específicos atribuídos a eles podem participar de reuniões e assumir uma das funções participantes descritas nas [funções dos participantes.](#participant-roles) O tipo de usuário não está incluído na API **getParticipantRole.**

Os seguintes tipos de usuário identificam o que cada usuário pode fazer e o que pode acessar:

* **In-tenant**: Os usuários in-tenant pertencem à organização e têm credenciais em Azure Active Directory (AAD) para o inquilino. Eles geralmente são funcionários em tempo integral, no local ou remotos. Um usuário inquilina pode ser um organizador, apresentador ou participante.
* **Convidado**: Um convidado é um participante de outra organização convidada a acessar Teams ou outros recursos no inquilino da organização. Os hóspedes são adicionados ao AAD da sua organização e têm os mesmos recursos de Teams que um membro nativo da equipe com acesso a bate-papos, reuniões e arquivos da equipe. Um usuário convidado pode ser um organizador, apresentador ou participante. Para obter mais informações, consulte [o acesso ao hóspede em Teams](/microsoftteams/guest-access).
* **Federado ou externo**: Um usuário federado é um usuário externo Teams em outra organização que foi convidada a participar de uma reunião. Esses usuários possuem credenciais válidas com parceiros federados e são autorizados pela Teams. Eles não têm acesso a suas equipes ou outros recursos compartilhados de sua organização. O acesso aos hóspedes é uma melhor opção para usuários externos terem acesso a equipes e canais. Para obter mais informações, consulte [gerenciar o acesso externo em Teams](/microsoftteams/manage-external-access).
* **Anônimos**: Usuários anônimos não têm identidade AAD e não são federados com um inquilino. O participante anônimo é como um usuário externo, mas sua identidade não é projetada na reunião. Um usuário anônimo não pode ser um organizador, mas pode ser um apresentador ou um participante.

> [!NOTE]
> Os usuários anônimos herdam a política global de permissão de aplicativos padrão do usuário. Para obter mais informações, consulte [Gerenciar aplicativos](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

A tabela a seguir fornece os tipos de usuário e quais recursos cada usuário pode acessar:

| Tipo de usuário | Guias | Bots | Extensões de mensagens | Cartões Adaptáveis | Módulos de tarefas | Caixa de diálogo na reunião |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Usuário anônimo | Não disponível | Não disponível | Não disponível | Interações no bate-papo de reunião são permitidas. | Interações no bate-papo de reunião de um Cartão Adaptável são permitidas. | Não disponível |
| Hóspede que faz parte do inquilino AAD | A interação é permitida. Não são permitidas a criação, atualização e exclusão. | Não disponível | Não disponível | Interações no bate-papo de reunião são permitidas. | Interações no bate-papo de reunião de um Cartão Adaptável são permitidas. | Disponível |
| Federado | Não disponível | Não disponível | Não disponível | Não disponível | Não disponível | Não disponível |

## <a name="see-also"></a>Confira também

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md)
* [Extensão de mensagem](../messaging-extensions/what-are-messaging-extensions.md)
* [Criar seu aplicativo](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar seu aplicativo](create-apps-for-teams-meetings.md)
