---
title: Habilitar e configurar seus aplicativos para Teams reuniões
author: surbhigupta
description: Habilitar e configurar seus aplicativos para reuniões Teams diferentes cenários de reunião, atualizar manifesto do aplicativo, configurar recursos, como, caixa de diálogo na reunião, estágio de reunião compartilhado, sidepanel de reunião e muito mais
ms.topic: conceptual
ms.localizationpriority: none
ms.openlocfilehash: 17dc9bce0bb6a54aea09d0f41b01840e5d2ca621
ms.sourcegitcommit: b9af51e24c9befcf46945400789e750c34723e56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62821588"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a>Habilitar e configurar seus aplicativos para Teams reuniões

Cada equipe tem uma maneira diferente de comunicar e colaborar tarefas. Para realizar essas tarefas diferentes, personalize Teams com aplicativos para reuniões. Habilita seus aplicativos Teams reuniões e configure os aplicativos para estar disponíveis no escopo de reunião no manifesto do aplicativo.

## <a name="enable-your-app-for-teams-meetings"></a>Habilitar seu aplicativo para Teams reuniões

Para habilitar seu aplicativo para reuniões Teams, atualize o manifesto do aplicativo e use as propriedades de contexto para determinar onde seu aplicativo deve aparecer.

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo usando `configurableTabs`as matrizes , `scopes`e `context` . O escopo define quem pode acessar e o contexto define onde seu aplicativo está disponível.

> [!NOTE]
> * Você deve atualizar o manifesto do aplicativo com o [esquema de manifesto](../resources/schema/manifest-schema-dev-preview.md).
> * Aplicativos em reuniões exigem `groupchat` escopo. O `team` escopo funciona apenas para guias em canais.

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

### <a name="context-property"></a>Propriedade Context

A `context` propriedade determina o que deve ser mostrado quando um usuário invoca um aplicativo em uma reunião, dependendo de onde o usuário invoca o aplicativo. A guia `context` e as `scopes` propriedades permitem determinar onde seu aplicativo deve aparecer. As guias no escopo ou `team` podem `groupchat` ter mais de um contexto. A seguir estão os valores da `context` propriedade da qual você pode usar todos ou alguns dos valores:

|Valor|Descrição|
|---|---|
| **channelTab** | Uma guia no header de um canal de equipe. |
| **privateChatTab** | Uma guia no header de um chat de grupo entre um conjunto de usuários, não no contexto de uma equipe ou reunião. |
| **meetingChatTab** | Uma guia no header de um chat de grupo entre um conjunto de usuários para uma reunião agendada. Você pode especificar **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingDetailsTab** | Uma guia no header da exibição de detalhes da reunião do calendário. Você pode especificar **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingSidePanel** | Um painel na reunião foi aberto por meio da barra unificada (U-bar). |
| **meetingStage** | Um aplicativo do pode `meetingSidePanel` ser compartilhado para o estágio de reunião. Você não pode usar este aplicativo em clientes móveis ou de sala do Teams. |

Depois de habilitar seu aplicativo para Teams reuniões, você deve configurar seu aplicativo antes de uma reunião, durante uma reunião e após uma reunião.

## <a name="configure-your-app-for-meeting-scenarios"></a>Configurar seu aplicativo para cenários de reunião

Teams reuniões fornecem uma experiência colaborativa para sua organização. Configure seu aplicativo para diferentes cenários de reunião e aprimora a experiência de reunião. Agora você pode identificar quais ações podem ser tomadas nos seguintes cenários de reunião:

* [Antes de uma reunião](#before-a-meeting)
* [Durante uma reunião](#during-a-meeting)
* [Após uma reunião](#after-a-meeting)

### <a name="before-a-meeting"></a>Antes de uma reunião

Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagens. Os usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.

**Para adicionar uma guia a uma reunião**

1. Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.
1. Selecione a **guia Detalhes** e selecione <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    <img src="../assets/images/apps-in-meetings/PreMeeting.png" alt="Pre-meeting experience" width="900"/>

1. Na galeria de guias exibida, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma guia.

**Para adicionar uma extensão de mensagens a uma reunião**

1. Selecione as releições &#x25CF;&#x25CF;&#x25CF; localizadas na área de mensagem de composição no chat.
1. Selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma extensão de mensagens.

**Para adicionar um bot a uma reunião**

Em um chat de reunião, insira a chave **@** e selecione **Obter bots**.

> [!NOTE]
> * A bolha de conteúdo publica um Cartão Adaptável ou um cartão simultaneamente no chat de reunião que os usuários podem acessar. Isso ajuda os usuários quando a reunião ou o aplicativo Teams é minimizado.
> * A identidade do usuário deve ser confirmada usando [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md). Após a autenticação, o aplicativo pode recuperar a função de usuário usando a `GetParticipant` API.
> * Com base na função de usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função. Por exemplo, um aplicativo de sondagem permite que apenas organizadores e apresentadores criem uma nova sondagem.
> * As atribuições de função podem ser alteradas enquanto uma reunião está em andamento. Para obter mais informações, [consulte funções em uma Teams reunião](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Durante uma reunião

Durante uma reunião, você pode usar a caixa `meetingSidePanel` de diálogo ou a caixa de diálogo na reunião para criar experiências exclusivas para seus aplicativos.

#### <a name="meeting-sidepanel"></a>Meeting SidePanel

O `meetingSidePanel` permite personalizar experiências em uma reunião que permite que organizadores e apresentadores tenham diferentes tipos de exibição e ações. No manifesto do aplicativo, você deve adicionar `meetingSidePanel` à matriz de contexto. Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia na reunião que tem 320 pixels de largura. Para obter mais informações, consulte [Interface FrameContext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).

Para usar a `userContext` API para rotear solicitações, [consulte Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Para obter mais informações, [consulte Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md). O fluxo de autenticação para guias é semelhante ao fluxo de autenticação para sites. Portanto, as guias podem usar o OAuth 2.0 diretamente. Para obter mais informações, [consulte plataforma de identidade da Microsoft fluxo de código de autorização do OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

A extensão de mensagens funciona conforme o esperado quando um usuário está em uma exibição de reunião. O usuário pode postar cartões de extensão de mensagem de composição. AppName in-meeting é uma dica de ferramenta que informa o nome do aplicativo na U-bar de reunião.

> [!NOTE]
> Use a versão 1.7.0 ou superior do [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), pois as versões anteriores a ele não suportam o painel lateral.

#### <a name="in-meeting-dialog-box"></a>Caixa de diálogo na reunião

A caixa de diálogo na reunião é usada para envolver os participantes durante a reunião e coletar informações ou comentários durante a reunião. Use a [API SendNotificationSignal](API-references.md#send-notification-signal-api) para disparar uma notificação de bolha. Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser mostrado está hospedado.

A caixa de diálogo na reunião não deve usar o módulo de tarefa. O módulo de tarefa não é invocado em um chat de reunião. Uma URL de recurso externo é usada para exibir a bolha de conteúdo em uma reunião. Você pode usar o método `submitTask` para enviar dados em um chat de reunião.

> [!NOTE]
> * Você deve invocar [a função submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submit-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no visualização da Web. Esse é um requisito para envio de aplicativo. Para obter mais informações, [consulte Teams módulo de tarefa do SDK](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true). 
> * Se você quiser que seu aplicativo suporte usuários anônimos, `from.id` a carga inicial de solicitação de invocação deve depender dos metadados `from` de solicitação no objeto, não de `from.aadObjectId` metadados de solicitação. `from.id`é a ID do usuário e `from.aadObjectId` é a Microsoft Azure Active Directory (Azure AD) ID do usuário. Para obter mais informações, [consulte using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

#### <a name="shared-meeting-stage"></a>Estágio de reunião compartilhada

O estágio de reunião compartilhado permite que os participantes da reunião interajam e colaborem no conteúdo do aplicativo em tempo real. Você pode compartilhar seus aplicativos para o estágio de reunião colaborativa das seguintes maneiras:

* [Compartilhar aplicativo inteiro em estágio](#share-entire-app-to-stage) usando o botão compartilhar para estágios no Teams cliente.
* [Compartilhe partes específicas do aplicativo em estágios](#share-specific-parts-of-the-app-to-stage) usando APIs no SDK Teams cliente.

##### <a name="share-entire-app-to-stage"></a>Compartilhar aplicativo inteiro em estágio

Os participantes podem compartilhar todo o aplicativo para o estágio de reunião colaborativa usando o botão compartilhar para o estágio do painel lateral do aplicativo.

<img src="../assets/images/apps-in-meetings/share_to_stage_during_meeting.png" alt="Share full app" width = "900"/>

Para compartilhar todo o aplicativo em estágio, no manifesto do aplicativo, você deve configurar `meetingStage` e como `meetingSidePanel` contextos de quadro. Por exemplo:

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

Para obter mais informações, consulte [manifesto do aplicativo](../resources/schema/manifest-schema-dev-preview.md#configurabletabs). 

##### <a name="share-specific-parts-of-the-app-to-stage"></a>Compartilhar partes específicas do aplicativo em estágio

Os participantes podem compartilhar partes específicas do aplicativo para o estágio de reunião colaborativa usando o compartilhamento para as APIs de estágio. As APIs estão disponíveis no SDK Teams cliente e são invocadas do painel lateral do aplicativo.

<img src="../assets/images/apps-in-meetings/share-specific-content-to-stage.png" alt="Share specific parts of the app" width = "900"/>

Para compartilhar partes específicas do aplicativo em estágio, você deve invocar as APIs relacionadas na biblioteca SDK do cliente Teams cliente. Para obter mais informações, consulte [Referência de API](API-references.md).

Se você quiser que seu aplicativo suporte usuários anônimos, `from.id` a carga inicial de solicitação de invocação deve depender dos metadados `from` de solicitação no objeto, não de `from.aadObjectId` metadados de solicitação. `from.id` é a ID do usuário e `from.aadObjectId` é a ID do Azure AD do usuário. Para obter mais informações, [consulte using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="after-a-meeting"></a>Após uma reunião

As configurações de depois e [antes das reuniões](#before-a-meeting) são as mesmas.

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Aplicativo de reunião | Demonstra como usar o aplicativo Gerador de Token de Reunião para solicitar um token. O token é gerado sequencialmente para que cada participante tenha uma oportunidade justa de contribuir em uma reunião. O token é útil em situações como reuniões scrum e&A. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
|Exemplo de estágio de reunião | Exemplo de aplicativo para mostrar uma guia no estágio de reunião para colaboração | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
|Painel do lado da reunião | Exemplo de aplicativo para mostrar como adicionar agenda em um painel do lado da reunião | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |-|

## <a name="step-by-step-guides"></a>Guias passo a passo

* Siga o [guia passo a passo para](../sbs-meeting-token-generator.yml) gerar o token de reunião em sua Teams reunião.
* Siga o [guia passo a passo para](../sbs-meetings-sidepanel.yml) gerar o sidepanel de reunião em sua Teams reunião.
* Siga o [guia passo a passo para](../sbs-meetings-stage-view.yml) gerar o exibição do estágio de reunião em sua reunião Teams reunião.
* Siga o [guia passo a passo para](../sbs-meeting-content-bubble.yml) gerar a bolha de conteúdo de reunião em sua Teams reunião.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Referências à API de aplicativos de reunião](API-references.md)

## <a name="see-also"></a>Confira também

* [Diretrizes de design de caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Diretrizes de design de experiência de reunião compartilhadas](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Adicionar aplicativos a reuniões por meio do Microsoft Graph](/graph/api/chat-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true)
