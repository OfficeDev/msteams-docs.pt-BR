---
title: Habilitar e configurar seus aplicativos para Teams reuniões
author: surbhigupta
description: Habilitar e configurar seus aplicativos para reuniões Teams diferentes cenários de reunião, atualizar o manifesto do aplicativo, configurar recursos, como caixa de diálogo na reunião, estágio de reunião compartilhado, sidepanel de reunião e muito mais
ms.topic: conceptual
ms.localizationpriority: none
ms.openlocfilehash: 4c3f571797df2810e76fc7145e9e9441adbd1e9b
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103345"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a>Habilitar e configurar seus aplicativos para Teams reuniões

Cada equipe tem uma maneira diferente de comunicar e colaborar tarefas. Para realizar essas tarefas diferentes, personalize Teams aplicativos para reuniões. Habilite seus aplicativos Teams reuniões e configure os aplicativos para que eles sejam disponibilizados no escopo da reunião no manifesto do aplicativo.

## <a name="prerequisites"></a>Pré-requisitos

Com aplicativos para Teams reuniões, você pode expandir os recursos de seus aplicativos em todo o ciclo de vida da reunião. Antes de trabalhar com aplicativos para Teams reuniões, você deve atender aos seguintes pré-requisitos:

* Saiba como desenvolver aplicativos Teams aplicativos. Para obter mais informações sobre como desenvolver Teams aplicativo, [consulte Teams desenvolvimento de aplicativos](../overview.md).

* Use seu aplicativo que dá suporte a guias configuráveis no escopo do groupchat. Para obter mais informações, consulte [o escopo do chat em grupo](../resources/schema/manifest-schema.md#configurabletabs) [e crie uma guia de grupo](../build-your-first-app/build-channel-tab.md).

* Siga as [diretrizes Teams design de guia geral para cenários](../tabs/design/tabs.md) pré e pós-reunião. Para experiências durante reuniões, consulte as [diretrizes de design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) da guia na reunião e as [diretrizes de design de diálogo na reunião](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades de evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios em todo o ciclo de vida da reunião. Para a caixa de diálogo na reunião, consulte `completionBotId` o parâmetro [na carga de notificação na reunião](API-references.md#send-an-in-meeting-notification).

## <a name="enable-your-app-for-teams-meetings"></a>Habilitar seu aplicativo para Teams reuniões

Para habilitar seu aplicativo para Teams reuniões, atualize o manifesto do aplicativo e use as propriedades de contexto para determinar onde seu aplicativo deve aparecer.

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

As funcionalidades do aplicativo de reuniões são declaradas no manifesto do aplicativo `configurableTabs`usando o , `scopes`e as `context` matrizes. O escopo define quem pode acessar e o contexto define onde seu aplicativo está disponível.

> [!NOTE]
>
> * Você deve atualizar o manifesto do aplicativo com o [esquema de manifesto](../resources/schema/manifest-schema-dev-preview.md).
> * Os aplicativos em reuniões exigem `groupchat` escopo. O `team` escopo funciona apenas para guias em canais.

O manifesto do aplicativo deve incluir o seguinte snippet de código:

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

A `context` propriedade determina o que deve ser mostrado quando um usuário invoca um aplicativo em uma reunião, dependendo de onde o usuário invoca o aplicativo. A guia `context` e as `scopes` propriedades permitem que você determine onde seu aplicativo deve aparecer. As guias no escopo ou no `team` escopo `groupchat` podem ter mais de um contexto.

Suporte ao `groupchat` escopo para habilitar seu aplicativo em chats pré-reunião e pós-reunião. Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar as tarefas de pré-reunião. Com a experiência de aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou taxa.

 A seguir estão os valores da `context` propriedade da qual você pode usar todos ou alguns dos valores:

|Valor|Descrição|
|---|---|
| **channelTab** | Uma guia no cabeçalho de um canal de equipe. |
| **privateChatTab** | Uma guia no cabeçalho de um chat em grupo entre um conjunto de usuários, não no contexto de uma equipe ou reunião. |
| **meetingChatTab** | Uma guia no cabeçalho de um chat em grupo entre um conjunto de usuários para uma reunião agendada. Você pode especificar **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingDetailsTab** | Uma guia no cabeçalho da exibição de detalhes da reunião do calendário. Você pode especificar **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingSidePanel** | Um painel na reunião aberto por meio da barra unificada (barra U). |
| **meetingStage** | Um aplicativo do pode `meetingSidePanel` ser compartilhado para o estágio da reunião. Você não pode usar este aplicativo em clientes móveis ou de sala do Teams. |

Depois de habilitar seu aplicativo para Teams reuniões, você deve configurar seu aplicativo antes de uma reunião, durante uma reunião e após uma reunião.

## <a name="configure-your-app-for-meeting-scenarios"></a>Configurar seu aplicativo para cenários de reunião

Teams reuniões fornecem uma experiência colaborativa para sua organização. Configure seu aplicativo para diferentes cenários de reunião e para aprimorar a experiência de reunião. Agora você pode identificar quais ações podem ser executadas nos seguintes cenários de reunião:

* [Antes de uma reunião](#before-a-meeting)
* [Durante uma reunião](#during-a-meeting)
* [Após uma reunião](#after-a-meeting)

### <a name="before-a-meeting"></a>Antes de uma reunião

Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagem. Os usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.

Para adicionar uma guia a uma reunião:

1. Em seu calendário, selecione uma reunião à qual você deseja adicionar uma guia.
1. Selecione a **guia Detalhes** e selecione <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    <img src="../assets/images/apps-in-meetings/PreMeeting.png" alt="Pre-meeting experience" width="900"/>

1. Na galeria de guias exibida, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma guia.

Para adicionar uma extensão de mensagem a uma reunião:

1. Selecione as reticências &#x25CF;&#x25CF;&#x25CF; localizadas na área de mensagem de composição no chat.
1. Selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma extensão de mensagem.

Para adicionar um bot a uma reunião:

Em um chat de reunião, insira a chave **@** e selecione **Obter bots**.

> [!NOTE]
> * A caixa de diálogo na reunião exibe uma caixa de diálogo em uma reunião e posta simultaneamente um Cartão Adaptável no chat de reunião que os usuários podem acessar. O Cartão Adaptável no chat de reunião ajuda os usuários durante a reunião ou se o Teams aplicativo está minimizado.
> * A identidade do usuário deve ser confirmada usando [o SSO do Tabs](../tabs/how-to/authentication/auth-aad-sso.md). Após a autenticação, o aplicativo pode recuperar a função de usuário usando a `GetParticipant` API.
> * Com base na função de usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função. Por exemplo, um aplicativo de sondagem permite que apenas organizadores e apresentadores criem uma nova votação.
> * As atribuições de função podem ser alteradas enquanto uma reunião está em andamento. Para obter mais informações, [consulte funções em uma Teams reunião](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Durante uma reunião

Durante uma reunião, você pode usar a notificação `meetingSidePanel` ou em reunião para criar experiências exclusivas para seus aplicativos.

#### <a name="meeting-sidepanel"></a>SidePanel da Reunião

Isso `meetingSidePanel` permite que você personalize experiências em uma reunião que permitem que organizadores e apresentadores tenham um conjunto diferente de exibições e ações. No manifesto do aplicativo, você deve adicionar à `meetingSidePanel` matriz de contexto. Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia na reunião que tem 320 pixels de largura. Para obter mais informações, consulte [a interface FrameContext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).

Para usar a `userContext` API para rotear solicitações, [consulte Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Para obter mais informações, [consulte Teams de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md). O fluxo de autenticação para guias é semelhante ao fluxo de autenticação para sites. Portanto, as guias podem usar o OAuth 2.0 diretamente. Para obter mais informações, [consulte plataforma de identidade da Microsoft fluxo de código de autorização do OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

A extensão de mensagem funciona conforme o esperado quando um usuário está em uma exibição em reunião. O usuário pode postar cartões de extensão de mensagem de composição. AppName em reunião é uma dica de ferramenta que indica o nome do aplicativo na U-bar da reunião.

> [!NOTE]
> Use a versão 1.7.0 ou superior do [SDK do Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), pois as versões anteriores a ele não dão suporte ao painel lateral.

#### <a name="in-meeting-notification"></a>Notificação na reunião

A notificação na reunião é usada para envolver os participantes durante a reunião e coletar informações ou comentários durante a reunião. Use uma [carga de notificação na reunião](API-references.md#send-an-in-meeting-notification) para disparar uma notificação na reunião. Como parte do conteúdo da solicitação de notificação, inclua a URL em que o conteúdo a ser mostrado está hospedado.

A notificação na reunião não deve usar o módulo de tarefa. O módulo de tarefa não é invocado em um chat de reunião. Uma URL de recurso externo é usada para exibir a notificação na reunião. Você pode usar o método `submitTask` para enviar dados em um chat de reunião.

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-dialogbox.png" alt-text="O exemplo mostra como você pode usar uma caixa de diálogo na reunião." border="true":::

#### <a name="shared-meeting-stage"></a>Estágio de reunião compartilhada

O estágio de reunião compartilhada permite que os participantes da reunião interajam e colaborem no conteúdo do aplicativo em tempo real. Você pode compartilhar seus aplicativos no estágio de reunião colaborativa das seguintes maneiras:

* [Compartilhe todo o aplicativo para preparar](#share-entire-app-to-stage) usando o botão compartilhar para preparar Teams cliente.
* [Compartilhe partes específicas do aplicativo para preparar](#share-specific-parts-of-the-app-to-stage) usando APIs no SDK do Teams cliente.

##### <a name="share-entire-app-to-stage"></a>Compartilhar aplicativo inteiro no estágio

Os participantes podem compartilhar todo o aplicativo para o estágio de reunião colaborativo usando o botão compartilhar para preparar no painel lateral do aplicativo.

<img src="../assets/images/apps-in-meetings/share_to_stage_during_meeting.png" alt="Share full app" width = "900"/>

Para compartilhar todo o aplicativo no estágio, no manifesto do aplicativo, você deve configurar `meetingStage` e como `meetingSidePanel` contextos de quadro. Por exemplo:

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

Os participantes podem compartilhar partes específicas do aplicativo para o estágio de reunião colaborativa usando o compartilhamento para preparar APIs. As APIs estão disponíveis no SDK do Teams cliente e são invocadas no painel lateral do aplicativo.

<img src="../assets/images/apps-in-meetings/share-specific-content-to-stage.png" alt="Share specific parts of the app" width = "900"/>

Para compartilhar partes específicas do aplicativo para preparar, você deve invocar as APIs relacionadas na biblioteca Teams SDK do cliente. Para obter mais informações, consulte referência [de API](API-references.md).

> [!NOTE]
> * Para compartilhar partes específicas do aplicativo para preparar, use Teams versão 1.12 ou posterior do manifesto.
> * Há suporte para o compartilhamento de partes específicas do aplicativo para estágio somente Teams clientes da área de trabalho.

### <a name="after-a-meeting"></a>Após uma reunião

As configurações de depois e [antes das reuniões](#before-a-meeting) são as mesmas.

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Aplicativo de reunião | Demonstra como usar o aplicativo Gerador de Token de Reunião para solicitar um token. O token é gerado sequencialmente para que cada participante tenha uma oportunidade justa de contribuir em uma reunião. O token é útil em situações como reuniões scrum e sessões de Q&A. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
|Exemplo de estágio de reunião | Aplicativo de exemplo para mostrar uma guia no estágio de reunião para colaboração | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
|Painel lateral da reunião | Aplicativo de exemplo para mostrar como adicionar a agenda em um painel do lado da reunião | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |-|

## <a name="step-by-step-guides"></a>Guias passo a passo

* Siga o [guia passo a passo para](../sbs-meeting-token-generator.yml) gerar o token de reunião em sua Teams reunião.
* Siga o [guia passo a passo para](../sbs-meetings-sidepanel.yml) gerar o painel lateral da reunião em sua Teams reunião.
* Siga o [guia passo a passo para](../sbs-meetings-stage-view.yml) compartilhar o modo de exibição do estágio de reunião em sua Teams reunião.
* Siga o [guia passo a passo para gerar](../sbs-meeting-content-bubble.yml) a bolha de conteúdo de reunião em sua Teams reunião.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Referências à API de aplicativos de reunião](API-references.md)

## <a name="see-also"></a>Confira também

* [Diretrizes de design da caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Diretrizes de design da experiência de estágio de reunião compartilhada](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Adicionar aplicativos a reuniões por meio do Microsoft Graph](/graph/api/chat-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true)
