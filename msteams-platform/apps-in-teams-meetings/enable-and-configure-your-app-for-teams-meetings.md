---
title: Habilitar e configurar seus aplicativos para reuniões do Teams
author: surbhigupta
description: Saiba como habilitar e configurar seus aplicativos para reuniões do Teams e diferentes cenários de reuniões, atualizar o manifesto de aplicativos, configurar recursos e muito mais.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: d00beadecbb2de2011a4cb6abbc94ce18a149eb1
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66557733"
---
# <a name="enable-and-configure-apps-for-meetings"></a>Habilitar e configurar aplicativos para reuniões

Cada equipe tem uma maneira diferente de comunicar e colaborar tarefas. Para realizar essas tarefas diferentes, personalize Teams com aplicativos para reuniões. Habilite seus aplicativos de reuniões do Teams e configure os aplicativos para que eles sejam disponibilizados no escopo da reunião no manifesto do aplicativo.

## <a name="prerequisites"></a>Pré-requisitos

Com aplicativos para reuniões do Teams, você pode expandir os recursos de seus aplicativos em todo o ciclo de vida da reunião. Antes de trabalhar com aplicativos para reuniões do Teams, você deve atender aos seguintes pré-requisitos:

* Saiba como desenvolver aplicativos do Teams. Para obter mais informações sobre como desenvolver o aplicativo do Teams, consulte [Desenvolvimento de aplicativos do Teams](../overview.md).

* Use seu aplicativo que dá suporte a guias configuráveis no escopo do groupchat. Para obter mais informações, consulte [o escopo do chat em grupo](../resources/schema/manifest-schema.md#configurabletabs) e [crie uma guia de grupo](../build-your-first-app/build-channel-tab.md).

* Siga as diretrizes gerais [Diretrizes de design de guia do Teams ](../tabs/design/tabs.md) para cenários pré e pós-reunião. Para experiências durante as reuniões, consulte as [diretrizes de design de guia na reunião ](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) e as [diretrizes de design de diálogo na reunião](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades de evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios em todo o ciclo de vida da reunião. Para a caixa de diálogo na reunião, consulte `completionBotId` o parâmetro em [carga de notificação na reunião](API-references.md#send-an-in-meeting-notification).

## <a name="enable-your-app-for-teams-meetings"></a>Habilitar seu aplicativo para reuniões do Teams

Para habilitar seu aplicativo para reuniões do Teams, atualize o manifesto do aplicativo e use as propriedades de contexto para determinar onde seu aplicativo deve aparecer.

### <a name="update-your-app-manifest"></a>Atualizar seu manifesto do aplicativo

As funcionalidades do aplicativo de reuniões são declaradas no manifesto do aplicativo usando o `configurableTabs`, `scopes`e as `context` matrizes. O escopo define quem pode acessar e o contexto define onde seu aplicativo está disponível.

> [!NOTE]
>
> * Os aplicativos em reuniões exigem `groupchat` escopo. O `team` escopo funciona apenas para guias em canais.
> * Os aplicativos em reuniões podem utilizar os seguintes contextos: `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel` e `meetingStage`

O trecho do código a seguir é um exemplo de guia configurável utilizada em um aplicativo para reuniões do Teams:

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

A `context` propriedade determina o que deve ser mostrado quando um usuário invoca um aplicativo em uma reunião, dependendo de onde o usuário invoca o aplicativo. A guia `context` e as `scopes` propriedades permitem que você determine onde seu aplicativo deve aparecer. As guias no `team` ou `groupchat` escopo podem ter mais de um contexto.

Suporte ao `groupchat` escopo para habilitar seu aplicativo em chats pré-reunião e pós-reunião. Com a experiência de aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar as tarefas de pré-reunião. Com a experiência do aplicativo de pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou taxa.

 A seguir estão os valores da `context` propriedade da qual você pode usar todos ou alguns dos valores:

|Valor|Descrição|
|---|---|
| **channelTab** | Uma guia no cabeçalho de um canal de equipe. |
| **privateChatTab** | Uma guia no cabeçalho de um chat em grupo entre um conjunto de usuários, não no contexto de uma equipe ou reunião. |
| **meetingChatTab** | Uma guia no cabeçalho de um chat em grupo entre um conjunto de usuários para uma reunião agendada. Você pode especificar o **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingDetailsTab** | Uma guia no cabeçalho da exibição de detalhes da reunião do calendário. Você pode especificar o **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingSidePanel** | Um painel na reunião aberto por meio da barra unificada (U-bar). |
| **meetingStage** | Um aplicativo do `meetingSidePanel` pode ser compartilhado no estágio da reunião. Você não pode usar este aplicativo em clientes móveis ou de sala do Teams. |

Depois de habilitar seu aplicativo para reuniões do Teams, você deve configurar seu aplicativo antes de uma reunião, durante uma reunião e após uma reunião.

## <a name="configure-your-app-for-meeting-scenarios"></a>Configurar seu aplicativo para cenários de reunião

As reuniões do Teams fornecem uma experiência colaborativa para sua organização. Configure seu aplicativo para diferentes cenários de reunião e para aprimorar a experiência de reunião. Agora você pode identificar quais ações podem ser executadas nos seguintes cenários de reunião:

* [Antes de uma reunião](#before-a-meeting)
* [Durante uma reunião](#during-a-meeting)
* [Após uma reunião](#after-a-meeting)

### <a name="before-a-meeting"></a>Antes de uma reunião

Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagem. Os usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.

Para adicionar uma guia a uma reunião:

1. Em seu calendário, selecione uma reunião à qual você deseja adicionar uma guia.
1. Selecione a guia **Detalhes** e selecione <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    <img src="../assets/images/apps-in-meetings/PreMeeting.png" alt="Pre-meeting experience" width="900"/>

1. Na galeria de guias exibida, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma guia.

Para adicionar uma extensão de mensagem a uma reunião:

1. Selecione as reticências &#x25CF;&#x25CF;&#x25CF; localizadas na área de mensagem de composição no chat.
1. Selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma extensão de mensagem.

Para adicionar um bot a uma reunião:

Em um chat de reunião, insira a **@** chave e selecione **Obter bots**.

> [!NOTE]
>
> * A caixa de diálogo na reunião exibe uma caixa de diálogo em uma reunião e posta simultaneamente um Cartão Adaptável no chat de reunião que os usuários podem acessar. O Cartão Adaptável no chat de reunião ajuda os usuários durante a reunião ou se o aplicativo do Teams está minimizado.
> * A identidade do usuário deve ser confirmada usando as [Guias do Tabs](../tabs/how-to/authentication/tab-sso-overview.md). Após a autenticação, o aplicativo pode recuperar a função de usuário usando a `GetParticipant` API.
> * Com base na função de usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função. Por exemplo, um aplicativo de sondagem permite que apenas organizadores e apresentadores criem uma nova votação.
> * As atribuições de função podem ser alteradas enquanto uma reunião está em andamento. Para obter mais informações, consulte [funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Durante uma reunião

Durante uma reunião, você pode usar a `meetingSidePanel` ou a notificação em reunião para criar experiências exclusivas para seus aplicativos.

#### <a name="meeting-sidepanel"></a>SidePanel da Reunião

A `meetingSidePanel` permite que você personalize experiências em uma reunião que permite que organizadores e apresentadores tenham um conjunto diferente de exibições e ações. No manifesto do aplicativo, você deve adicionar à `meetingSidePanel` matriz de contexto. Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia na reunião que tem 320 pixels de largura. Para obter mais informações, consulte [Interface do FrameContext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).

Para usar a `userContext` API para rotear solicitações, consulte [Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Para obter mais informações, consulte [Fluxo de autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md). O fluxo de autenticação para guias é semelhante ao fluxo de autenticação para sites. Portanto, as guias podem usar o OAuth 2.0 diretamente. Para obter mais informações, consulte [Fluxo de código de autorização OAuth 2.0 e a plataforma de identidade da Microsoft](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

A extensão de mensagem funciona conforme o esperado quando um usuário está em uma exibição em reunião. O usuário pode postar cartões de extensão de mensagem de composição. AppName em reunião é uma dica de ferramenta que indica o nome do aplicativo na U-bar da reunião.

> [!NOTE]
> Use a versão 1.7.0 ou superior do [SDK do Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), pois as versões anteriores a ele não dão suporte ao painel lateral.

#### <a name="in-meeting-notification"></a>Notificação na reunião

A notificação na reunião é usada para envolver os participantes durante a reunião e coletar informações ou comentários durante a reunião. Use uma [carga de notificação na reunião](API-references.md#send-an-in-meeting-notification) para disparar uma notificação na reunião. Como parte do conteúdo da solicitação de notificação, inclua a URL em que o conteúdo a ser mostrado está hospedado.

A notificação na reunião não deve usar o módulo de tarefa. O módulo de tarefa não é invocado em um chat de reunião. Uma URL de recurso externo é usada para exibir a notificação na reunião. Você pode usar o `submitTask` método para enviar dados em um chat de reunião.

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-dialogbox.png" alt-text="O exemplo mostra como você pode usar uma caixa de diálogo na reunião.":::

#### <a name="shared-meeting-stage"></a>Estágio de reunião compartilhada

O estágio de reunião compartilhada permite que os participantes da reunião interajam e colaborem no conteúdo do aplicativo em tempo real. Você pode compartilhar seus aplicativos no estágio de reunião colaborativa das seguintes maneiras:

* [Compartilhe todo o aplicativo para preparar](#share-entire-app-to-stage) usando o botão compartilhar para preparar o cliente do Teams.
* [Compartilhe partes específicas do aplicativo para preparar](#share-specific-parts-of-the-app-to-stage) usando APIs no SDK do cliente do Teams.

##### <a name="share-entire-app-to-stage"></a>Compartilhar aplicativo inteiro no estágio

Os participantes podem compartilhar todo o aplicativo para o estágio de reunião colaborativo usando o botão compartilhar para preparar no painel lateral do aplicativo.

<img src="../assets/images/apps-in-meetings/share_to_stage_during_meeting.png" alt="Share full app" width = "900"/>

Para compartilhar todo o aplicativo no estágio, no manifesto do aplicativo, você deve configurar `meetingStage` e `meetingSidePanel` como contextos de quadro. Por exemplo:

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

Para obter mais informações, consulte o [manifesto do aplicativo](../resources/schema/manifest-schema-dev-preview.md#configurabletabs).

##### <a name="share-specific-parts-of-the-app-to-stage"></a>Compartilhar partes específicas do aplicativo para preparar

Os participantes podem compartilhar partes específicas do aplicativo para o estágio de reunião colaborativa usando o compartilhamento para preparar APIs. As APIs estão disponíveis no SDK do cliente do Teams e são invocadas no painel lateral do aplicativo.

<img src="../assets/images/apps-in-meetings/share-specific-content-to-stage.png" alt="Share specific parts of the app" width = "900"/>

Para compartilhar partes específicas do aplicativo para preparar, você deve invocar as APIs relacionadas na biblioteca SDK do cliente do Teams. Para obter mais informações, consulte a [referência da API](API-references.md).

> [!NOTE]
>
> * Para compartilhar partes específicas do aplicativo para preparar, use a versão 1.12 ou posterior do manifesto do Teams.
> * Há suporte para o compartilhamento de partes específicas do aplicativo para estágio somente dos clientes da área de trabalho do Teams.

### <a name="after-a-meeting"></a>Após uma reunião

As configurações de depois e [antes das reuniões](#before-a-meeting) são as mesmas.

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Aplicativo de reunião | Demonstra como usar o aplicativo Gerador de Token de Reunião para solicitar um token. O token é gerado sequencialmente para que cada participante tenha uma oportunidade justa de contribuir em uma reunião. O token é útil em situações como reuniões scrum e sessões de P e R. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
|Exemplo de estágio de reunião | Aplicativo de exemplo para mostrar uma guia no estágio de reunião para colaboração | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
|Painel lateral da reunião | Aplicativo de exemplo para mostrar como adicionar a agenda em um painel lateral da reunião | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |-|

## <a name="step-by-step-guides"></a>Guias passo a passo

* Siga o [guia passo a passo](../sbs-meeting-token-generator.yml) para gerar o token de reunião em sua reunião do Teams.
* Siga o [guia passo a passo para](../sbs-meetings-sidepanel.yml) gerar o painel lateral da reunião em sua reunião do Teams.
* Siga o [guia passo a passo](../sbs-meetings-stage-view.yml) para compartilhar o modo de exibição do estágio de reunião em sua reunião do Teams.
* Siga o [guia passo a passo](../sbs-meeting-content-bubble.yml) para gerar a bolha de conteúdo de reunião em sua reunião do Teams.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Referências à API de aplicativos de reunião](API-references.md)

## <a name="see-also"></a>Confira também

* [Diretrizes de design da caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Fluxo de autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Diretrizes de design da experiência de estágio de reunião compartilhada](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Adicionar aplicativos a reuniões por meio do Microsoft Graph](/graph/api/chat-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true)
