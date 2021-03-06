---
title: Habilitar e configurar seus aplicativos para Teams reuniões
author: surbhigupta
description: Habilitar e configurar seus aplicativos para Teams reuniões
ms.topic: conceptual
ms.openlocfilehash: 16112b75e109702f1f0be6d335b8d407d35211b5
ms.sourcegitcommit: 3560ee1619e3ab6483a250f1d7f2ceb69353b2dc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/08/2021
ms.locfileid: "53335365"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a>Habilitar e configurar seus aplicativos para Teams reuniões

Cada equipe tem uma maneira diferente de comunicar e colaborar tarefas. Você pode realizar essas tarefas diferentes personalização Teams aplicativos para reuniões. Para personalizar e realizar tarefas diferentes, você deve habilitar seus aplicativos para reuniões Teams e configurar seus aplicativos para estar disponível no escopo de reunião no manifesto do aplicativo.

## <a name="enable-your-app-for-teams-meetings"></a>Habilitar seu aplicativo para Teams reuniões

Para habilitar seu aplicativo para reuniões Teams, você deve atualizar o manifesto do aplicativo e usar as propriedades de contexto para determinar onde seu aplicativo deve aparecer.

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo usando `configurableTabs` `scopes` as matrizes , e `context` . O escopo define a quem e o contexto define onde seu aplicativo está disponível.

> [!NOTE]
> * Tente atualizar o manifesto do aplicativo com o [esquema de manifesto](../resources/schema/manifest-schema-dev-preview.md).
> * Os aplicativos em reuniões exigem escopo de groupchat. O escopo da equipe funciona apenas para guias em canais.

O manifesto do aplicativo deve incluir o seguinte trecho de código:

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "team",
        "groupchat"
      ],
      "context":[
        "channelTab",
        "privateChatTab",
        "meetingChatTab",
        "meetingDetailsTab",
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```

> [!NOTE]
> `meetingStage` está disponível no momento apenas na [visualização do](../resources/dev-preview/developer-preview-intro.md) desenvolvedor.

### <a name="context-property"></a>Propriedade Context

A propriedade determina o que deve ser mostrado quando um usuário invoca um aplicativo em uma reunião, dependendo de onde o usuário `context` invoca o aplicativo. A guia `context` e `scopes` as propriedades permitem determinar onde seu aplicativo deve aparecer. Guias no `team` escopo ou podem `groupchat` ter mais de um contexto. A seguir estão os valores da propriedade da qual você pode usar todos ou `context` alguns dos valores:

|Valor|Descrição|
|---|---|
| **channelTab** | Uma guia no header de um canal de equipe. |
| **privateChatTab** | Uma guia no header de um chat de grupo entre um conjunto de usuários, não no contexto de uma equipe ou reunião. |
| **meetingChatTab** | Uma guia no header de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada. Você pode especificar **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingDetailsTab** | Uma guia no header da exibição de detalhes da reunião do calendário. Você pode especificar **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingSidePanel** | Um painel na reunião foi aberto por meio da barra unificada (U-bar). |
| **meetingStage** | Um aplicativo do meetingSidePanel pode ser compartilhado no estágio de reunião. Essa guia não é suportada no celular. |

Depois de habilitar seu aplicativo para Teams reuniões, você deve configurar seu aplicativo antes de uma reunião, durante uma reunião e após uma reunião.

## <a name="configure-your-app-for-meeting-scenarios"></a>Configurar seu aplicativo para cenários de reunião

> [!NOTE]
> Para que seu aplicativo seja visível na galeria de guias, ele deve dar suporte a guias configuráveis e ao escopo de chat de grupo.

Teams reuniões fornece uma experiência colaborativa exclusiva para sua organização. Ele oferece a oportunidade de configurar seu aplicativo para diferentes cenários de reunião. Você pode configurar seus aplicativos para aprimorar a experiência de reunião com base na função de participante ou no tipo de usuário. Agora você pode identificar quais ações podem ser tomadas nos seguintes cenários de reunião:

* [Antes de uma reunião](#before-a-meeting)
* [Durante uma reunião](#during-a-meeting)
* [Após uma reunião](#after-a-meeting)

### <a name="before-a-meeting"></a>Antes de uma reunião

Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagens. Os usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.

**Para adicionar uma guia a uma reunião**

1. Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.
1. Selecione a **guia Detalhes** e selecione <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    ![Experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

1. Na galeria de guias exibida, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma guia.

    > [!NOTE]
    > Atualmente, na guia reuniões, não há suporte para obter detalhes da reunião e informações dos participantes.

**Para adicionar uma extensão de mensagens a uma reunião**

1. Selecione as releições &#x25CF;&#x25CF;&#x25CF; localizadas na área de mensagem de composição no chat.
1. Selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma extensão de mensagens.

**Para adicionar um bot a uma reunião**

Em um chat de reunião, insira a **@** chave e selecione Obter **bots**.

> [!NOTE]
> * A identidade do usuário deve ser confirmada usando [Guias SSO](../tabs/how-to/authentication/auth-aad-sso.md). Após a autenticação, o aplicativo pode recuperar a função de usuário usando a `GetParticipant` API.
> * Com base na função de usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função. Por exemplo, um aplicativo de sondagem permite que apenas organizadores e apresentadores criem uma nova sondagem.
> * As atribuições de função podem ser alteradas enquanto uma reunião está em andamento. Para obter mais informações, [consulte funções em uma Teams reunião](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Durante uma reunião

Durante uma reunião, você pode usar a caixa de diálogo meetingSidePanel ou in-meeting para criar experiências exclusivas para seus aplicativos.

#### <a name="meetingsidepanel"></a>meetingSidePanel

Com o meetingSidePanel, você pode personalizar experiências em uma reunião que permite que os organizadores e apresentadores tenham diferentes tipos de exibição e ações. No manifesto do aplicativo, você deve adicionar meetingSidePanel à matriz de contexto. Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia na reunião que tem 320 pixels de largura. Para obter mais informações, consulte [Interface FrameContext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).

Para usar a `userContext` API para rotear solicitações de acordo, [consulte Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Para obter mais informações, [consulte Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md). O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites. Portanto, as guias podem usar o OAuth 2.0 diretamente. Para obter mais informações, consulte plataforma de identidade da Microsoft fluxo de código de autorização [do OAuth 2.0 e do OAuth 2.0.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)

A extensão de mensagens funciona conforme o esperado quando um usuário está em uma exibição em reunião e o usuário pode postar cartões de extensão de mensagem de composição. AppName in-meeting é uma dica de ferramenta que informa o nome do aplicativo na U-bar de reunião.

> [!NOTE]
> Use a versão 1.7.0 ou superior do [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)pois as versões anteriores a ele não suportam o painel lateral.

#### <a name="in-meeting-dialog-box"></a>Caixa de diálogo na reunião

A caixa de diálogo na reunião pode ser usada para envolver os participantes durante a reunião e coletar informações ou comentários durante a reunião. Use a [`NotificationSignal`](create-apps-for-teams-meetings.md#notificationsignal-api) API para sinalizar que uma notificação de bolha deve ser disparada. Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser mostrado está hospedado.

A caixa de diálogo na reunião não deve usar o módulo de tarefa. O módulo de tarefa não é invocado em um chat de reunião. Uma URL de recurso externo é usada para exibir a bolha de conteúdo em uma reunião. Você pode usar o `submitTask` método para enviar dados em um chat de reunião.

> [!NOTE]
> * Você deve invocar [a função submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submit-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no visualização da Web. Esse é um requisito para envio de aplicativo. Para obter mais informações, consulte Teams módulo de tarefa [do SDK.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)
> * Se você quiser que seu aplicativo suporte usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos metadados de solicitação no objeto, não `from.id` `from` nos `from.aadObjectId` metadados de solicitação. `from.id`é a ID do usuário `from.aadObjectId` e é a ID Azure Active Directory (AAD) do usuário. Para obter mais informações, [consulte using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

#### <a name="shared-meeting-stage"></a>Estágio de reunião compartilhado

> [!NOTE]
> * Esse recurso está disponível apenas na visualização [do](../resources/dev-preview/developer-preview-intro.md) desenvolvedor.

O estágio de reunião compartilhado permite que os participantes da reunião interajam e colaborem no conteúdo do aplicativo em tempo real.

O contexto necessário está `meetingStage` no manifesto do aplicativo. Um pré-requisito para isso é ter o `meetingSidePanel` contexto. Isso habilita **o Compartilhamento** no meetingSidePanel.

![Compartilhar em estágios durante a experiência de reunião](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

Para habilitar o estágio de reunião compartilhada, configure o manifesto do aplicativo desta forma:

```json
"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "groupchat"
      ],
      "context":[
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```

Veja como projetar [uma experiência de estágio de reunião compartilhada.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)

### <a name="after-a-meeting"></a>Após uma reunião

As configurações após e [antes das reuniões](#before-a-meeting) são as mesmas.

## <a name="code-sample"></a>Exemplo de código

|Exemplo de nome | Descrição | Amostra |
|----------------|-----------------|--------------|----------------|-----------|
| Aplicativo de reunião | Demonstra como usar o aplicativo Gerador de Tokens de Reunião para solicitar um token, que é gerado sequencialmente para que cada participante tenha uma oportunidade justa de contribuir em uma reunião. Isso pode ser útil em situações como reuniões scrum e&A. | [View](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token) |

## <a name="see-also"></a>Confira também

* [Diretrizes de design de caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
