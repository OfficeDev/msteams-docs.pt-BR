---
title: Extensibilidade do aplicativo de reunião
author: surbhigupta
description: Compreender a extensibilidade do aplicativo de reunião
ms.topic: conceptual
ms.openlocfilehash: 0daa3b1976754eff6fed057de0c3659b51506f96
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068633"
---
# <a name="meeting-app-extensibility"></a>Extensibilidade do aplicativo de reunião

Teams extensibilidade do aplicativo de reunião baseia-se nos seguintes conceitos:

* O ciclo de vida da reunião tem estágios diferentes, como pré-reunião, reunião e pós-reunião.  
* Há três funções de participantes distintas em uma reunião: organizador, apresentador e participante. Para obter mais informações, [consulte funções em uma Teams reunião](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).  
* Há vários tipos [de usuário](/microsoftteams/non-standard-users#:~:text=An%20anonymous%20user%20is%20a,their%20Microsoft%20or%20organization's%20account.) em uma reunião: no locatário, [convidado,](/microsoftteams/guest-access) [federado](/microsoftteams/manage-external-access)e usuários anônimos.

Este artigo aborda informações sobre o ciclo de vida da reunião e como integrar guias, bots e extensões de mensagens na reunião. Ele fornece informações para identificar diferentes funções de participante e diferentes tipos de usuário para executar tarefas.

## <a name="meeting-lifecycle"></a>Ciclo de vida da reunião

O ciclo de vida da reunião consiste na experiência do aplicativo de pré-reunião, na reunião e pós-reunião. Você pode integrar guias, bots e extensões de mensagens em cada estágio do ciclo de vida da reunião.

### <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrar guias ao ciclo de vida da reunião

As guias permitem que os membros da equipe acessem serviços e conteúdo em um espaço específico dentro de uma reunião. A equipe trabalha diretamente com guias e tem conversas sobre as ferramentas e dados disponíveis nas guias. Na Teams, os usuários podem adicionar uma guia selecionando <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>e escolhendo o aplicativo que eles querem instalar.

> [!IMPORTANT]
> Se você tiver integrado uma guia à sua reunião Teams, seu aplicativo deverá seguir o fluxo de autenticação de logom único [(SSO)](../tabs/how-to/authentication/auth-aad-sso.md)para guias .

> [!NOTE]
> * Os clientes móveis suportam guias somente em estágios pré e pós-reunião. As experiências em reunião que estão na caixa de diálogo e no painel da reunião não estão disponíveis no momento em dispositivos móveis.
> * Os aplicativos têm suporte apenas em reuniões agendadas privadas.

#### <a name="pre-meeting-app-experience"></a>Experiência do aplicativo de pré-reunião

Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar tarefas de pré-reunião, como desenvolver uma sondagem para participantes da reunião de pesquisa.

**Para adicionar guias a uma reunião existente**

1. Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.
1. Selecione a **guia Detalhes** e selecione <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. A galeria de guias é exibida.

    ![Experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

1. Na galeria de guias, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma guia.

    ![Exibição de guia de pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

    > [!NOTE]
    > * Você também pode adicionar uma guia usando a guia **Chat de** reunião em uma reunião existente.
    > * O layout da guia deve estar em um estado organizado, se houver mais de dez pesquisas ou pesquisas.

#### <a name="in-meeting-app-experience"></a>Experiência do aplicativo na reunião

Com a experiência do aplicativo na reunião, você pode envolver os participantes durante a reunião usando aplicativos e a caixa de diálogo na reunião. Os aplicativos de reunião são hospedados na barra superior superior da janela de reunião como uma guia na reunião. Use a caixa de diálogo na reunião para mostrar conteúdo a actionable para os participantes da reunião. Para obter mais informações, [consulte create apps for Teams meetings](create-apps-for-teams-meetings.md).

**Para usar guias durante uma reunião**

1. Depois de inserir a reunião, na barra superior superior da janela de chat, selecione o aplicativo que você deseja usar. Um aplicativo fica visível em uma reunião Teams no painel lateral ou na caixa de diálogo na reunião.
1. Na caixa de diálogo na reunião, insira sua resposta como um feedback.

    ![Exibição da caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

    > [!NOTE]
    > * Os aplicativos podem aproveitar Teams SDK do cliente para acessar `meetingId` o , `userMri` e `frameContext` renderizar a experiência adequadamente.
    > * Se a caixa de diálogo na reunião for renderizada com êxito, você será notificado de que os resultados foram baixados com êxito.
    > * O manifesto do aplicativo especifica os locais onde você deseja que eles apareçam. O campo de contexto é usado para essa finalidade. Ele também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeito a diretrizes de design especificadas.

    A imagem a seguir ilustra o painel do lado da reunião:

    ![Painel do lado da reunião](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="post-meeting-app-experience"></a>Experiência de aplicativo pós-reunião

Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários. Selecionar <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/> para adicionar uma guia e obter notas de reunião e resultados sobre quais organizadores e participantes devem tomar medidas.

A imagem a seguir exibe a **guia Contoso** com resultados da sondagem e comentários recebidos dos participantes da reunião:

![Exibição pós-reunião](../assets/images/apps-in-meetings/PostMeeting.png)

> [!NOTE]
> O layout da guia deve ser organizado quando houver mais de dez pesquisas ou pesquisas.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrar bots ao ciclo de vida da reunião

Os bots habilitados no escopo de groupchat começam a funcionar em reuniões. Para implementar bots, comece com [a criação](../build-your-first-app/build-bot.md) de um bot e continue com a criação [de aplicativos para Teams reuniões.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-references)

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrar extensões de mensagens ao ciclo de vida da reunião

Para implementar extensões de mensagens, comece com [a](../messaging-extensions/how-to/create-messaging-extension.md) criação de uma extensão de mensagens e continue com a criação de [aplicativos para Teams reuniões.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-references)

A Teams extensibilidade do aplicativo de reunião permite que você projete seu aplicativo com base nas funções dos participantes em uma reunião.

## <a name="participant-roles-in-a-meeting"></a>Funções de participante em uma reunião

![Participantes de uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

As configurações de participante padrão são determinadas pelo administrador de IT de uma organização. Veja a seguir as funções dos participantes em uma reunião:

* **Organizador**: o organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião. Somente usuários com conta M365 e Teams licença podem ser organizadores e controlar permissões do participante. Um organizador da reunião pode alterar as configurações de uma reunião específica. Os organizadores podem fazer essas alterações na página da Web **opções de** reunião.
* **Apresentador :** os apresentadores têm os mesmos recursos de organizadores com exclusões. Um apresentador não pode remover um organizador da sessão ou modificar opções de reunião para a sessão. Por padrão, os participantes que participam de uma reunião têm a função de apresentador.
* **Participante**: um participante é um usuário que foi convidado a participar de uma reunião, mas não está autorizado a atuar como apresentador. Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma das configurações de reunião ou compartilhar conteúdo.

> [!NOTE]
> Somente um organizador ou apresentador pode adicionar, remover ou desinstalar aplicativos.

Para obter mais informações, [consulte funções em uma Teams reunião](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Depois de projetar seu aplicativo com base nas funções de participantes em uma reunião, você pode identificar cada tipo de usuário para reuniões e selecionar o que eles podem acessar.

## <a name="user-types-in-a-meeting"></a>Tipos de usuário em uma reunião

> [!NOTE]
> O tipo de usuário não está incluído na API **getParticipantRole.**

Tipos de usuário, como, organizador, apresentador ou participante em uma reunião podem executar uma das funções de [participante em uma reunião](#participant-roles-in-a-meeting).

A lista a seguir detalha os diferentes tipos de usuário, juntamente com sua acessibilidade e desempenho:

* **In-tenant**: Os usuários no locatário pertencem à organização e têm credenciais Azure Active Directory (AAD) para o locatário. Eles geralmente são funcionários em tempo integral, no local ou remotos. Um usuário no locatário pode ser um organizador, apresentador ou participante.
* **Convidado**: um convidado é um participante de outra organização convidado para acessar Teams ou outros recursos no locatário da organização. Os convidados são adicionados ao AAD da organização e têm os mesmos Teams de um membro da equipe nativo com acesso a chats, reuniões e arquivos de equipe. Um usuário convidado pode ser organizador, apresentador ou participante. Para obter mais informações, consulte [acesso de convidados em Teams](/microsoftteams/guest-access).
* **Federado ou externo**: um usuário federado é um usuário externo Teams em outra organização que foi convidado a participar de uma reunião. Os usuários federados têm credenciais válidas com parceiros federados e são autorizados por Teams. Eles não têm acesso às suas equipes ou a outros recursos compartilhados da sua organização. O acesso de convidados é uma opção melhor para usuários externos ter acesso a equipes e canais. Para obter mais informações, consulte [manage external access in Teams](/microsoftteams/manage-external-access).

    > [!NOTE]
    > Os Teams podem adicionar aplicativos quando hospedam reuniões ou chats com outras organizações. Os usuários podem usar aplicativos compartilhados por usuários externos quando seus usuários ingressarem em reuniões ou chats hospedados por outras organizações. As políticas de dados da organização do usuário de hospedagem, bem como as práticas de compartilhamento de dados dos aplicativos de terceiros compartilhados pela organização desse usuário, estarão em vigor.

* **Anônimo**: os usuários anônimos não têm uma identidade AAD e não são federados com um locatário. Os participantes anônimos são como usuários externos, mas sua identidade não é projetada na reunião. Os usuários anônimos não podem acessar aplicativos em uma janela de reunião. Um usuário anônimo não pode ser organizador, mas pode ser apresentador ou participante.

    > [!NOTE]
    > Os usuários anônimos herdam a política de permissão de aplicativo padrão global no nível do usuário. Para obter mais informações, consulte [manage Apps](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

Um usuário convidado ou anônimo não pode adicionar, remover ou desinstalar aplicativos.

A tabela a seguir fornece os tipos de usuário e quais recursos cada usuário pode acessar:

| Tipo de usuário | Guias | Bots | Extensões de mensagens | Cartões Adaptáveis | Módulos de tarefas | Caixa de diálogo na reunião |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Usuário anônimo | Não disponível | Não disponível | Não disponível | Interações no chat de reunião são permitidas. | Interações no chat de reunião de um Cartão Adaptável são permitidas. | Não disponível |
| Convidado que faz parte do locatário AAD | A interação é permitida. Não é permitido criar, atualizar e excluir. | Não disponível | Não disponível | Interações no chat de reunião são permitidas. | Interações no chat de reunião de um Cartão Adaptável são permitidas. | Disponível |
| Usuário federado. Para obter mais informações, consulte [usuários não padrão](/microsoftteams/non-standard-users). | A interação é permitida. Não é permitido criar, atualizar e excluir. | A interação é permitida. Não é permitido adquirir, atualizar e excluir. | Não disponível | Interações no chat de reunião são permitidas. | Interações no chat de reunião de um Cartão Adaptável são permitidas. | Não disponível |

## <a name="see-also"></a>Confira também

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md)
* [Extensão de mensagem](../messaging-extensions/what-are-messaging-extensions.md)
* [Criar seu aplicativo](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Pré-requisitos e referências de API para aplicativos de reuniões do Teams](create-apps-for-teams-meetings.md)