---
title: Aplicativos para reuniões do Teams
author: surbhigupta
description: Neste artigo, saiba como os aplicativos funcionam em reuniões do Microsoft Teams com base na extensibilidade de aplicativos e funções de usuário e participantes.
ms.topic: overview
ms.author: lajanuar
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: b98204e1aec3224cad5955a1682d3d5338c47084
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615167"
---
# <a name="apps-for-teams-meetings-and-calls"></a>Aplicativos para reuniões e chamadas do Teams

As reuniões permitem colaboração, parceria, comunicação informada e comentários compartilhados. O espaço de reunião pode fornecer uma experiência do usuário para cada estágio do ciclo de vida da reunião. A ilustração a seguir fornece a você uma ideia dos recursos de extensibilidade do aplicativo de reuniões:

:::image type="content" source="../assets/images/apps-in-meetings/meetingappextensibility.png" alt-text="A captura de tela mostra como funciona a extensibilidade do aplicativo de reunião.":::

Você deve estar familiarizado com os seguintes conceitos de produto para criar experiências de reunião personalizadas com aplicativos no Microsoft Teams.

## <a name="supported-meeting-types-in-teams"></a>Tipos de reunião com suporte no Teams

O Teams dá suporte ao acesso a aplicativos durante a reunião para os seguintes tipos de reunião:

* [**Reuniões agendadas**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop): reuniões agendadas por meio do calendário do Teams.
* [**Reuniões de canal agendadas**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop): reuniões agendadas por meio de canais públicos do Teams.
* [**Chamadas um-a-um**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): chamadas iniciadas em chat um-a-um.
* [**Chamadas em grupo**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): chamadas iniciadas no chat em grupo.
* [**Reuniões instantâneas**](https://support.microsoft.com/office/start-an-instant-meeting-in-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5): reuniões iniciadas **por meio do botão Reunir agora** no calendário do Teams.
* [**Webinar**](https://support.microsoft.com/office/get-started-with-teams-webinars-42f3f874-22dc-4289-b53f-bbc1a69013e3): Webinar iniciado por meio do **botão Webinar** na **lista suspensa Nova** Reunião.

Saiba mais sobre [reuniões, expiração e políticas](/MicrosoftTeams/meeting-expiration) e reuniões do Teams [, webinars e eventos ao vivo](/microsoftteams/quick-start-meetings-live-events).
> [!NOTE]
>
> * No momento, os aplicativos para reuniões de canal público agendadas estão disponíveis apenas na [versão prévia do desenvolvedor público](../resources/dev-preview/developer-preview-intro.md).
> * Os aplicativos não são compatíveis com o seguinte:
>   * [Chamadas PSTN (Rede Telefônica Pública Comunada)](/microsoftteams/cloud-voice-landing-page#public-switched-telephone-network-connectivity-options)
>   * [Chamadas do Teams criptografadas de ponta a ponta](https://support.microsoft.com/office/use-end-to-end-encryption-for-teams-calls-1274b4d2-b5c5-4b24-a376-606fa6728a90)
>   * [Reuniões instantâneas de canal](https://support.microsoft.com/office/start-an-instant-meeting-in-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5)
>   * Reuniões no [canal compartilhado](https://support.microsoft.com/office/what-is-a-shared-channel-in-teams-e70a8c22-fee4-4d6e-986f-9e0781d7d11d)

## <a name="meeting-lifecycle"></a>Ciclo de vida da reunião

Um ciclo de vida de reunião inclui experiência de aplicativo de pré-reunião, em reunião e pós-reunião, dependendo do tipo de usuário e da função do usuário em uma reunião do Teams.

## <a name="user-types-in-teams"></a>Tipos de usuário no Teams

O Teams dá suporte a tipos de usuário, como no locatário, convidado, federado ou usuário externo em uma reunião do Teams. Cada tipo de usuário pode ter uma das funções [de usuário na reunião do Teams](#user-roles-in-teams-meeting).

> [!NOTE]
>
> Atualmente, quando uma terceira pessoa é adicionada a uma chamada um-a-um, a chamada é elevada a uma chamada de grupo que significa que uma nova sessão é iniciada. Os aplicativos adicionados à chamada um-a-um não estão disponíveis na chamada de grupo. No entanto, eles podem ser adicionados novamente.

A lista a seguir detalha os vários tipos de usuário juntamente com sua acessibilidade:

* **No locatário**: os usuários no locatário pertencem à organização e têm credenciais no AAD (Azure Active Directory) para o locatário. Eles são funcionários em tempo integral, no local ou remotos. Um usuário no locatário pode ser um organizador, apresentador ou participante.
* **Convidado**: um convidado é um participante de outra organização convidado para acessar o Teams ou outros recursos no locatário da organização. Os convidados são adicionados ao ambiente da Azure AD e têm os mesmos recursos do Teams que um membro nativo da equipe. Eles têm acesso a chats, reuniões e arquivos da equipe. Um convidado pode ser um organizador, apresentador ou participante. Para obter mais informações, consulte [o acesso de convidados no Teams](/microsoftteams/guest-access).
* **Federado ou externo**: um usuário federado ou externo é um usuário do Teams de outra organização que foi convidado a ingressar em uma reunião. Os usuários federados têm credenciais válidas com parceiros federados e são autorizados pelo Teams. Eles não têm acesso ao Teams ou a outros recursos compartilhados da sua organização. O acesso de convidados é uma opção melhor para que usuários externos tenham acesso ao Teams e aos canais. Para obter mais informações, consulte [gerenciar o acesso externo no Teams](/microsoftteams/manage-external-access).

    > [!NOTE]
    > Os usuários do Teams podem adicionar aplicativos quando hospedam reuniões ou chats com outras organizações. Quando um usuário externo compartilha aplicativos na reunião, todo o usuário pode acessar o aplicativo. As políticas de dados da organização host e as práticas de compartilhamento de dados dos aplicativos de terceiros compartilhados pela organização desse usuário entrarão em vigor.

* **Anônimo**: os usuários anônimos não têm uma Azure AD identidade e não são federados com um locatário. Os participantes anônimos são como usuários externos, mas sua identidade não é mostrada na reunião. Usuários anônimos não podem acessar aplicativos em uma janela de reunião. Um usuário anônimo pode ser um apresentador ou um participante, mas não pode ser um organizador.

    > [!NOTE]
    > Os usuários anônimos herdam a política de permissão de aplicativo padrão global no nível do usuário. Para obter mais informações, consulte [gerenciar aplicativos](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

## <a name="user-roles-in-teams-meeting"></a>Funções de usuário na reunião do Teams

A seguir estão as funções de usuário em uma reunião do Teams:

* **Organizador**: o organizador agenda uma reunião, define as opções da reunião, atribui funções de reunião, controla as permissões do participante e inicia a reunião. Somente usuários com uma conta do Microsoft 365 e licença do Teams podem ser o organizador. Um organizador da reunião pode alterar as configurações de uma reunião específica na página [**opções da** reunião](https://support.microsoft.com/en-us/office/change-participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e).

* **Apresentador**: Os apresentadores em uma reunião têm recursos semelhantes aos do organizador, com exceção de remover um organizador da sessão e modificar as opções de reunião para a sessão.

* **Participante**: um participante é um usuário que é convidado a participar da reunião. Os participantes têm funcionalidades limitadas durante a reunião.

> [!NOTE]
> Somente um organizador ou apresentador pode adicionar, remover ou desinstalar aplicativos.

Para obter mais informações, consulte [funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

> [!TIP]
>
> * As [configurações de participante padrão são determinadas](/microsoftteams/meeting-policies-participants-and-guests) pelo administrador de TI de uma organização.De acordo com as configurações padrão, os participantes que ingressam em uma reunião têm a função de apresentador.
> * A função de apresentador não está disponível em chamadas um-a-um.
> * Um usuário que inicia a chamada de grupo de um chat é considerado organizador.

> [!IMPORTANT]
>
> * Atualmente, os aplicativos de terceiros estão disponíveis na GCC (Nuvem da Comunidade Governamental), mas não estão disponíveis para locatários do GCC-High e do Departamento de Defesa (DOD).
> * Aplicativos de terceiros são desativados por padrão para GCC. Para ativar aplicativos de terceiros para GCC, consulte [gerenciar políticas de permissão de aplicativo](/microsoftteams/teams-app-permission-policies) e [gerenciar aplicativos](/microsoftteams/manage-apps).

## <a name="see-also"></a>Confira também

* [Projetando sua extensão de reunião do Microsoft Teams](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Criar guias para reunião](~/apps-in-teams-meetings/build-tabs-for-meeting.md)
* [Criar aplicativos para o estágio de reunião do Teams](build-apps-for-teams-meeting-stage.md)
* [Criar conversa extensível para chat de reunião](build-extensible-conversation-for-meeting-chat.md)
* [Criar aplicativos para usuários anônimos](build-apps-for-anonymous-user.md)
* [APIs de aplicativos de reunião](meeting-apps-apis.md)
* [Colaboração aprimorada com o SDK do Live Share](teams-live-share-overview.md)
* [Cenas personalizadas do Modo Conferência](~/apps-in-teams-meetings/teams-together-mode.md)
