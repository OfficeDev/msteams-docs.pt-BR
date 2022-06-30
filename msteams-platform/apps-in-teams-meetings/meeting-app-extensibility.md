---
title: Aplicativos de reuniões unificadas
author: surbhigupta
description: Saiba mais sobre o ciclo de vida da reunião do Teams e a experiência de reunião dos usuários na área de trabalho e dispositivos móveis, tipos de usuário, integração de bots e extensão de mensagens no ciclo de vida da reunião.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 4c53567530f0d9d418a6b273200f921517341e7f
ms.sourcegitcommit: 779aa3220f6448a9dbbaea57e667ad95b5c39a2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66561620"
---
# <a name="unified-meetings-apps"></a>Aplicativos de reuniões unificadas

Os aplicativos de reuniões unificadas do Teams se baseiam nos seguintes conceitos:

* O ciclo de vida da reunião tem diferentes estágios: pré-reunião, reunião e pós-reunião.  
* Há três funções distintas de participante em uma reunião: organizador, apresentador e participante. Para obter mais informações, consulte [funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).  
* Há vários tipos [de usuário](/microsoftteams/non-standard-users#:~:text=An%20anonymous%20user%20is%20a,their%20Microsoft%20or%20organization's%20account.) em uma reunião: no locatário, [convidado](/microsoftteams/guest-access), [federado](/microsoftteams/manage-external-access) e usuários anônimos.

Este artigo aborda as informações sobre o ciclo de vida da reunião e como integrar guias, bots e extensões de mensagem. Ele identifica diferentes funções de participante e tipos de usuário.

## <a name="meeting-lifecycle"></a>Ciclo de vida da reunião

Um ciclo de vida de reunião consiste em experiência de aplicativos de pré-reunião, em reunião e pós-reunião. Você pode integrar guias, bots e extensões de mensagens em cada estágio do ciclo de vida da reunião.

> [!NOTE]
>
> * No momento, os aplicativos para reuniões instantâneas, um para um e chamadas de grupo estão disponíveis apenas na [versão prévia do desenvolvedor público](../resources/dev-preview/developer-preview-intro.md).
>
> * Há suporte para extensões de reunião, como bots, cartões, extensões de mensagem e ações de mensagem no cliente Web. No entanto, as experiências hospedadas, como guias, bolhas de conteúdo e compartilhamento em estágios, não têm suporte total no momento.

### <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrar guias ao ciclo de vida da reunião

As guias permitem que os membros da equipe acessem serviços e conteúdo em um espaço específico dentro de uma reunião. A equipe trabalha diretamente com guias e tem conversas sobre as ferramentas e os dados disponíveis nas guias. Na reunião do Teams, você pode adicionar uma guia selecionando <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>e selecione o aplicativo que você deseja instalar.

> [!IMPORTANT]
> Se você tiver integrado uma guia à sua reunião, seu aplicativo deverá seguir o fluxo de autenticação de SSO (logon único) do Teams [para guias](../tabs/how-to/authentication/tab-sso-overview.md).

> [!NOTE]
>
> * Não há suporte para adicionar a opção de aplicativo para o aplicativo de guia de extensão de reunião do Teams no cliente Web do Teams.

#### <a name="pre-meeting-app-experience"></a>Experiência de aplicativo de pré-reunião

Com a experiência de aplicativo de pré-reunião, os usuários podem encontrar e adicionar aplicativos de reunião. Os usuários também podem executar tarefas de pré-reunião, como desenvolver uma votação para pesquisar os participantes da reunião.

Para adicionar guias a uma reunião existente:

1. Em seu calendário, selecione uma reunião à qual você deseja adicionar uma guia.
1. Selecione a guia **Detalhes** e selecione <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. A galeria de guias é exibida.

    :::image type="content" source="~/assets/images/apps-in-meetings/Pre-Meeting-002.png" alt-text="Experiência de aplicativo de pré-reunião.":::

1. Na galeria de guias, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma guia.

   > [!NOTE]
   >
   > * Você também pode adicionar uma guia a uma reunião existente usando a guia **Chat da** reunião.
   > * O layout da guia deve estar em um estado organizado, se houver mais de 10 pesquisas ou pesquisas.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/PreMeetingTab.png" alt-text="Guias durante uma reunião.":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

Depois de adicionar as guias a uma reunião existente no celular, você poderá ver os mesmos aplicativos na experiência de pré-reunião  na seção Mais detalhes da reunião.

<img src="../assets/images/apps-in-meetings/mobilePostMeeting.png" alt="Mobile pre-meeting experience" width="200"/>  

---

#### <a name="in-meeting-app-experience"></a>Experiência de aplicativo na reunião

Com a experiência do aplicativo na reunião, você pode envolver os participantes durante a reunião usando aplicativos e a caixa de diálogo na reunião. Os aplicativos de reunião são hospedados na barra de ferramentas da janela de reunião como uma guia na reunião. Use a caixa de diálogo na reunião para demonstrar conteúdo acionável para os participantes nela. Para obter mais informações, consulte [Habilitar e configurar seus aplicativos para reuniões do Teams](enable-and-configure-your-app-for-teams-meetings.md).

Para dispositivos móveis, os aplicativos de reunião estão disponíveis em **Aplicativos** > reticências &#x25CF;&#x25CF;&#x25CF; na reunião. Selecione **Aplicativos** para exibir todos os aplicativos disponíveis na reunião.

Para área de trabalho, você pode adicionar aplicativos durante uma reunião usando **a** :::image type="icon" source="../assets/icons/add-icon.png" border="false"::: opção Adicionar um aplicativo na janela da reunião.

Para usar guias durante uma reunião:

1. Vá para o Teams.
1. Em seu calendário, selecione uma reunião na qual você deseja usar uma guia.
1. Depois de entrar na reunião, na barra de ferramentas da janela de chat, selecione o aplicativo necessário.
    Um aplicativo é visível em uma reunião do Teams no painel lateral ou na caixa de diálogo na reunião.
1. Na caixa de diálogo na reunião, insira sua resposta como comentários.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/desktop-in-meeting-dialog-view.png" alt-text="Exibição da área de trabalho na reunião.":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

Depois de entrar na reunião e adicionar o aplicativo da área de trabalho ou da Web, o aplicativo fica visível na reunião móvel do Teams na **seção Aplicativos** . Selecione **Aplicativos** para mostrar a lista de aplicativos. O usuário pode iniciar qualquer um dos aplicativos como um painel lateral na reunião do aplicativo.

A caixa de diálogo na reunião é exibida, na qual você pode inserir sua resposta como comentários.

<img src="../assets/images/apps-in-meetings/mobile-in-meeting-dialog-view.png" alt="Mobile dialog box view" width="200"/>

> [!NOTE]
> Você não precisa alterar o manifesto do aplicativo para que os aplicativos funcionem em dispositivos móveis.

---

> [!NOTE]
>
> * Os aplicativos podem aproveitar o SDK `meetingId`do Cliente do Teams para acessar e `userMri``frameContext` renderizar a experiência adequadamente.
> * Se a caixa de diálogo na reunião for renderizada com êxito, ela enviará uma notificação de que os resultados foram baixados com êxito.
> * O manifesto do aplicativo especifica os locais em que você deseja que os aplicativos apareçam. Isso pode ser feito especificando o campo de contexto no manifesto. Ele também faz parte de uma experiência de estágio de reunião de compartilhamento, sujeito às diretrizes de [design especificadas](~\apps-in-teams-meetings\design\designing-apps-in-meetings.md).
> * Não há suporte para o estágio de reunião para usuários anônimos e cliente Web do Teams.

A imagem a seguir ilustra o painel lateral na reunião:

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Painel lateral na reunião](../assets/images/in-meeting-dialog.png)

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

<img src="../assets/images/apps-in-meetings/sidepanelmobile.png" alt="In-meeting side panel mobile" width="300"/>

---

A tabela a seguir descreve o comportamento do aplicativo quando ele é validado e não validado:

|Funcionalidade do aplicativo | O aplicativo é validado | O aplicativo não é validado |
|---|---|---|
| Extensibilidade da reunião | O aplicativo aparecerá em reuniões. | O aplicativo não aparecerá em reuniões para os clientes móveis. |

Para obter mais informações, consulte [as diretrizes de validação do repositório](../concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).

#### <a name="post-meeting-app-experience"></a>Experiência de aplicativo pós-reunião

Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários. Selecionar <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/> para adicionar uma guia, obter anotações da reunião e ver os resultados nos quais organizadores e participantes devem tomar medidas.

A imagem a seguir exibe a **guia Contoso** com os resultados da votação e comentários recebidos dos participantes da reunião:

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/post.png" alt-text="Guia Contoso com resultados.":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="~/assets/images/apps-in-meetings/mobilepremeeting.png" alt-text="Experiência pós-aplicativo de reunião.":::

---

> [!NOTE]
> O layout da guia deve ser organizado quando houver mais de 10 pesquisas ou pesquisas.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrar bots ao ciclo de vida da reunião

Os bots habilitados no escopo do chat em grupo começam a funcionar em reuniões. Para implementar bots, comece com [a compilação de um bot](../build-your-first-app/build-bot.md) e continue com a [criação de aplicativos para reuniões do Teams](../apps-in-teams-meetings/API-references.md#meeting-apps-api-references).

### <a name="integrate-message-extensions-into-the-meeting-lifecycle"></a>Integrar extensões de mensagem ao ciclo de vida da reunião

Para implementar a extensão de mensagem, comece [com a criação de](../messaging-extensions/how-to/create-messaging-extension.md) uma extensão de mensagem e continue com a criação [de aplicativos para reuniões do Teams](../apps-in-teams-meetings/API-references.md#meeting-apps-api-references).

Os aplicativos de reuniões unificadas do Teams permitem que você projete seu aplicativo com base nas funções de participantes em uma reunião.

## <a name="participant-roles-in-a-meeting"></a>Funções de participante em uma reunião

:::image type="content" source="~/assets/images/apps-in-meetings/participant-roles.png" alt-text="Funções de participante em uma reunião.":::

As configurações de participante padrão são determinadas pelo administrador de TI de uma organização. A seguir estão as funções de participante em uma reunião:

* **Organizador**: o organizador agenda uma reunião, define as opções da reunião, atribui funções de reunião e inicia a reunião. Os usuários com a conta do Microsoft 365 e a licença do Teams só podem ser os organizadores e controlar as permissões dos participantes. Um organizador da reunião pode alterar as configurações de uma reunião específica. Os organizadores podem fazer essas alterações na página **da Web de opções da** Reunião.

* **Apresentador:** os apresentadores têm os mesmos recursos dos organizadores com exclusões. Um apresentador não pode remover um organizador da sessão ou modificar as opções de reunião da sessão. Por padrão, os participantes que ingressam em uma reunião têm a função de apresentador.

* **Participante**: um participante é um usuário que é convidado a participar da reunião. Os participantes têm recursos limitados durante a reunião, como:
  * Eles podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma das configurações da reunião nem compartilhar o conteúdo.  
  * Eles podem exibir ou interagir com o aplicativo guia no estágio da reunião no cliente da área de trabalho do Teams sem instalar o aplicativo ou sem quaisquer direitos de aplicativo. Eles não podem exibir ou interagir com o aplicativo no estágio da reunião em um cliente Web do Teams.
  * Eles não podem exibir ou interagir com o aplicativo no painel lateral sem quaisquer direitos de aplicativo.
  * Eles não estão autorizados a atuar como apresentadores.
  * Se o participante ingressar como um usuário anônimo, ele não poderá exibir ou interagir com o aplicativo guia no estágio da reunião em clientes web e de área de trabalho do Teams.

> [!NOTE]
> Somente um organizador ou apresentador pode adicionar, remover ou desinstalar aplicativos.

Para obter mais informações, consulte [funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Depois de projetar seu aplicativo com base nas funções de participante em uma reunião, você pode identificar cada tipo de usuário para reuniões e selecionar o que eles podem acessar.

## <a name="user-types-in-a-meeting"></a>Tipos de usuário em uma reunião

Tipos de usuário, como no locatário, convidado, federado ou usuário externo em uma reunião, podem fazer uma das funções de [participante em uma reunião](#participant-roles-in-a-meeting).

> [!NOTE]
> O tipo de usuário não está incluído na API **getParticipantRole** .

A lista a seguir detalha os vários tipos de usuário, juntamente com sua acessibilidade e desempenho:

* **No locatário**: os usuários no locatário pertencem à organização e têm credenciais Microsoft Azure Active Directory (Azure AD) para o locatário. Eles são funcionários em tempo integral, no local ou remotos. Um usuário no locatário pode ser um organizador, apresentador ou participante.
* **Convidado**: um convidado é um participante de outra organização convidado para acessar o Teams ou outros recursos no locatário da organização. Os convidados são adicionados ao ambiente da Azure AD e têm os mesmos recursos do Teams que um membro nativo da equipe. Eles têm acesso a chats, reuniões e arquivos da equipe. Um convidado pode ser um organizador, apresentador ou participante. Para obter mais informações, consulte [o acesso de convidados no Teams](/microsoftteams/guest-access).
* **Federado ou externo**: um usuário federado é um usuário externo do Teams em outra organização que foi convidado a ingressar em uma reunião. Os usuários federados têm credenciais válidas com parceiros federados e são autorizados pelo Teams. Eles não têm acesso às suas equipes ou a outros recursos compartilhados da sua organização. O acesso de convidados é uma opção melhor para que os usuários externos tenham acesso a equipes e canais. Para obter mais informações, consulte [gerenciar o acesso externo no Teams](/microsoftteams/manage-external-access).

    > [!NOTE]
    > Os usuários do Teams podem adicionar aplicativos quando hospedam reuniões ou chats com outras organizações. Os usuários podem usar aplicativos compartilhados por usuários externos quando seus usuários ingressam em reuniões ou chats hospedados por outras organizações. As políticas de dados da organização do usuário de hospedagem, bem como as práticas de compartilhamento de dados dos aplicativos de terceiros compartilhados pela organização desse usuário, estarão em vigor.

    > [!IMPORTANT]
    > Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e DoD (Departamento de Defesa). Aplicativos de terceiros são desativados por padrão para GCC. Para ativar aplicativos de terceiros para GCC, consulte [gerenciar políticas de permissão de aplicativo](/microsoftteams/teams-app-permission-policies) e [gerenciar aplicativos](/microsoftteams/manage-apps).

* **Anônimo**: os usuários anônimos não têm uma Azure AD identidade e não são federados com um locatário. Os participantes anônimos são como usuários externos, mas sua identidade não é mostrada na reunião. Os usuários anônimos não podem acessar aplicativos em uma janela de reunião e em um estágio de reunião. Um usuário anônimo não pode ser um organizador, mas pode ser um apresentador ou participante.

    > [!NOTE]
    > Os usuários anônimos herdam a política de permissão de aplicativo padrão global no nível do usuário. Para obter mais informações, consulte [gerenciar aplicativos](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

A tabela a seguir fornece os tipos de usuário e lista os recursos que cada usuário pode acessar em reuniões agendadas:

| Tipo de usuário | Guias | Bots | Extensões de mensagens | Cartões Adaptáveis | Módulos de tarefas | Caixa de diálogo na reunião | Estágio da reunião |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Usuário anônimo | Não disponível | Não disponível | Não disponível | Interações no chat da reunião são permitidas. | Interações no chat de reunião do Cartão Adaptável são permitidas. | Não disponível | Não disponível |
| Convidado, parte do locatário Azure AD | A interação é permitida. Criar, atualizar e excluir não são permitidos. | Não disponível | Não disponível | Interações no chat da reunião são permitidas. | Interações no chat de reunião do Cartão Adaptável são permitidas. | Disponível | Pode iniciar, exibir e interagir com o aplicativo no estágio da reunião somente no cliente da área de trabalho do Teams |
| Usuários federados, para obter mais informações, consulte [usuários não padrão](/microsoftteams/non-standard-users). | A interação é permitida em reuniões agendadas. Criar, atualizar e excluir não são permitidos. | A interação é permitida. A aquisição, a atualização e a exclusão não são permitidas. | Não disponível | Interações no chat da reunião são permitidas. | Interações no chat de reunião do Cartão Adaptável são permitidas. | Não disponível | Pode iniciar, exibir e interagir com o aplicativo no estágio da reunião somente no cliente da área de trabalho do Teams. |

> [!NOTE]
>
> O comportamento dos vários tipos de usuário para aplicativos em chamadas é idêntico ao seu comportamento em reuniões agendadas, com exceção do seguinte:
>
> * Os usuários federados não podem interagir com aplicativos de tabulação em chamadas.
> * Se os usuários federados forem adicionados a uma chamada existente com usuários no locatário ou convidados, todos os participantes perderão a capacidade de adicionar, atualizar ou remover aplicativos. No entanto, somente os usuários convidados ou no locatário existentes ainda poderão interagir com os aplicativos que foram adicionados antes de convidar usuários federados para a chamada.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Ative e configure seus aplicativos para reuniões do Teams](enable-and-configure-your-app-for-teams-meetings.md)

## <a name="see-also"></a>Confira também

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md)
* [Extensão de mensagem](../messaging-extensions/what-are-messaging-extensions.md)
* [Criar seu aplicativo](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Relatório de participação de reuniões do Microsoft Teams](/microsoftteams/teams-analytics-and-reports/meeting-attendance-report)
