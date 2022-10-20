---
title: Criar guias para reunião
author: surbhigupta
description: Saiba como criar guias para um chat de reunião, painel lateral de reunião e estágio de reunião na reunião do Microsoft Teams.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.date: 04/07/2022
ms.openlocfilehash: d86f0931cb6338ef331f2afe3a4a5fdb217bb316
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615365"
---
# <a name="build-tabs-for-meeting"></a>Criar guias para reunião

Cada equipe tem uma maneira diferente de comunicar e colaborar tarefas. Para realizar essas tarefas diferentes, personalize Teams com aplicativos para reuniões. Habilite seus aplicativos para reuniões do Teams e configure os aplicativos para que eles sejam disponibilizados no escopo da reunião no manifesto do aplicativo.

## <a name="tabs-in-teams-meetings"></a>Guias em reuniões do Teams

As guias permitem que os participantes da reunião acessem serviços e conteúdo em um espaço específico dentro de uma reunião. Se você for novo no desenvolvimento de guias do Microsoft Teams, confira [As guias Criar para o Teams](/microsoftteams/platform/tabs/what-are-tabs).

Antes de criar uma guia de reunião, é importante saber mais sobre as superfícies que estão disponíveis para direcionar o modo de exibição de chat da reunião, o modo de exibição de detalhes da reunião, o modo de exibição do painel lateral da reunião e o modo de exibição do estágio da reunião.

### <a name="meeting-details-view"></a>Exibição de detalhes da reunião

1. Em seu calendário, selecione uma reunião à qual você deseja adicionar uma guia.
1. Selecione a **guia Detalhes** e selecione :::image type="icon" source="../assets/icons/add-icon.png" Border = "false":::. A galeria de aplicativos é exibida.

   :::image type="content" source="~/assets/images/apps-in-meetings/Pre-Meeting-002.png" alt-text="Esta captura de tela mostra a experiência do aplicativo de pré-reunião na reunião do Teams.":::

1. Na galeria de aplicativos, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. A guia é adicionada à página de detalhes da reunião.

# <a name="desktop"></a>[Desktop](#tab/desktop)

A imagem a seguir mostra uma guia adicionada à página de detalhes da reunião no cliente da área de trabalho do Teams:

   :::image type="content" source="~/assets/images/apps-in-meetings/PreMeetingTab.png" alt-text="A captura de tela mostra as guias do Teams da área de trabalho na exibição de detalhes da reunião na reunião do Teams.":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

A imagem a seguir mostra uma guia adicionada à página de detalhes da reunião no cliente móvel do Teams:

   :::image type="content" source="../assets/images/mobile-tab.png" alt-text="A captura de tela mostra as guias móveis do Teams na exibição de detalhes da reunião na reunião do Teams.":::

---

### <a name="meeting-chat-view"></a>Modo de exibição de chat de reunião

1. No painel de chat do Teams, selecione o modo de exibição de chat da reunião.

1. Selecione e :::image type="icon" source="../assets/icons/add-icon.png" Border = "false"::: a galeria de aplicativos será exibida.

1. Na galeria de aplicativos, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. A guia é adicionada ao chat da reunião.

   :::image type="content" source="../assets/images/apps-in-meetings/meeting-chat-view.png" alt-text="A captura de tela mostra o modo de exibição de chat da reunião na reunião do Teams.":::

### <a name="meeting-side-panel-view"></a>Exibição do painel lateral da reunião

1. Durante uma reunião, você pode selecionar **Aplicativos** :::image type="icon" source="../assets/icons/add-icon.png" Border = "false"::: na janela de reunião do Teams para adicionar aplicativos à reunião.

   :::image type="content" source="../assets/images/apps-in-meetings/add-app.png" alt-text="Esta captura de tela mostra como adicionar um aplicativo na janela de reunião do Teams.":::

1. Na galeria de aplicativos, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é adicionado ao painel lateral da reunião.

   :::image type="content" source="../assets/images/side-panel-view.png" alt-text="Esta captura de tela mostra a exibição do painel lateral com a lista de aplicativos.":::

### <a name="meeting-stage-view"></a>Modo de exibição de estágio de reunião

1. Depois que uma guia é adicionada ao painel lateral da reunião, agora você pode optar por aceitar o compartilhamento global de aplicativos.

1. Isso resulta na guia renderização no estágio para cada participante da reunião.

   :::image type="content" source="../assets/images/meeting-stage-view.png" alt-text="Esta captura de tela mostra o modo de exibição de estágio de reunião do aplicativo que você compartilhou com a reunião.":::

### <a name="apps-in-channel-meeting"></a>Aplicativos na reunião do canal

Uma reunião de canal agendada pública tem a mesma lista de aplicativos que sua equipe pai. Instalar um aplicativo em uma reunião de canal também o disponibiliza na equipe pai e vice-versa.

No entanto, as instâncias de tabulação em uma reunião de canal são separadas das guias no próprio canal. Por exemplo, suponha que *um canal de* desenvolvimento tenha uma *guia polly* . Se você criar uma *reunião de standup* nesse canal, essa reunião não terá uma guia *polly* até que você adicione explicitamente a [guia à reunião](#meeting-details-view).

Em reuniões de canal agendadas públicas, depois que uma guia de reunião é adicionada, você pode selecionar o objeto de reunião na página de detalhes da reunião para acessar a guia.

:::image type="content" source="~/assets/images/apps-in-meetings/after-a-meeting1.png" alt-text="Após uma reunião":::

> [!NOTE]
> No celular, os usuários anônimos não podem acessar aplicativos em reuniões de canal público agendadas.

### <a name="app-manifest-settings-for-tabs-in-meeting"></a>Configurações de manifesto do aplicativo para guias na reunião

Atualize o [manifesto do aplicativo](/microsoftteams/platform/resources/schema/manifest-schema) com a propriedade de contexto relevante para configurar os diferentes modos de exibição de guia. As funcionalidades do aplicativo de reuniões são declaradas no manifesto do aplicativo usando os escopos e matrizes de contexto na seção configurableTabs.

#### <a name="scope"></a>Escopo

O escopo define quem pode acessar os aplicativos.

* `groupchat` O escopo  disponibiliza seu aplicativo em um escopo de grupo e permite que o aplicativo seja adicionado em uma chamada ou reunião (reunião privada agendada ou reuniões instantâneas).

* `team` scope makes your app available in a team scope and enables your app to be added in team or channel or scheduled channel meeting.

#### <a name="context"></a>Context

A `context` propriedade determina se o aplicativo está disponível no modo de exibição específico após a instalação e a configuração. A seguir estão os valores da `context` propriedade da qual você pode usar todos ou alguns dos valores:

|Valor|Descrição|
|---|---|
| **channelTab** | Uma guia no cabeçalho de um canal de equipe. |
| **privateChatTab** | Uma guia no cabeçalho de um chat em grupo entre um conjunto de usuários, não no contexto de uma equipe ou reunião. |
| **meetingChatTab** | Uma guia no cabeçalho de um chat em grupo entre um conjunto de usuários para uma reunião agendada. Você pode especificar o **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingDetailsTab** | Uma guia no cabeçalho da exibição de detalhes da reunião do calendário. Você pode especificar o **meetingChatTab** ou **meetingDetailsTab** para garantir que os aplicativos funcionem em dispositivos móveis. |
| **meetingSidePanel** | Um painel na reunião aberto por meio da barra unificada (U-bar). |
| **meetingStage** | Um aplicativo do `meetingSidePanel` pode ser compartilhado no estágio da reunião. Você não pode usar este aplicativo em clientes móveis ou de sala do Teams. |

#### <a name="configure-tab-app-for-a-meeting"></a>Configurar o aplicativo guia para uma reunião

Os aplicativos em reuniões podem utilizar os seguintes contextos: `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel` e `meetingStage` Depois que um participante da reunião instala um aplicativo e configura a guia na reunião, todos os outros contextos direcionados do aplicativo para a reunião determinada começam a renderizar a guia.

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

---

#### <a name="other-examples"></a>Outros exemplos

O contexto padrão para guias (se não for especificado) é:  

```json
"context":[ 
  "channelTab", 
  "privateChatTab", 
  "meetingChatTab", 
  "meetingDetailsTab" 
     ] 
```

Para impedir que um aplicativo seja exibido em chats de grupo que não são de reunião, você deve definir o seguinte contexto:

```json
"context":[ 
  "meetingSidePanel", 
  "meetingChatTab", 
  "meetingDetailsTab" 
     ] 
```

Somente para a experiência do painel lateral na reunião:  

```json
"context":[ 
  "meetingSidePanel" 
     ] 
```

### <a name="advanced-tab-sdk-apis"></a>APIs avançadas do SDK da guia

O SDK do cliente JavaScript do Microsoft Teams é um SDK avançado usado para criar guias usando JavaScript. Use o TeamsJS mais recente (V.2.0 ou posterior) para trabalhar no Teams, no Office e no Outlook. Para mais informações, veja o [Cliente SDK JavaScript do Teams](/microsoftteams/platform/tabs/how-to/using-teams-client-sdk?tabs=javascript%2Cmanifest-teams-toolkit).

### <a name="frame-context"></a>Contexto de quadro

A biblioteca JavaScript do Microsoft Teams expõe o frameContext no qual a URL da guia de reunião é carregada na API getContext. Os valores possíveis de frameContext são conteúdo, tarefa, configuração, remoção, sidePanel e meetingStage. Isso permite que você crie experiências personalizadas com base em onde o aplicativo é renderizado. Por exemplo, mostrando uma interface do usuário `meetingStage` específica voltada para colaboração quando na interface do usuário de preparação de reunião e em uma interface do usuário de preparação de reunião diferente na guia de chat (`content`). Para obter mais informações, consulte [a API getContext](/microsoftteams/platform/tabs/how-to/access-teams-context?tabs=teamsjs-v2).

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Aplicativo de reunião | Demonstra como usar o aplicativo Gerador de Token de Reunião para solicitar um token. O token é gerado sequencialmente para que cada participante tenha uma oportunidade justa de contribuir em uma reunião. O token é útil em situações como reuniões scrum e sessões de P e R. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Exemplo de estágio de reunião | Aplicativo de exemplo para mostrar uma guia no estágio de reunião para colaboração | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
| Painel lateral da reunião | Aplicativo de exemplo para mostrar como adicionar a agenda em um painel lateral da reunião | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |-|
| Notificação na reunião | Demonstra como implementar a notificação na reunião usando o bot. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs) |
| Assinatura de documento na reunião | Demonstra como implementar um aplicativo do Teams de assinatura de documentos. Inclui o compartilhamento de conteúdo específico do aplicativo para o estágio, o SSO do Teams e o modo de exibição de estágio específico do usuário. | [View](https://github.com/officedev/microsoft-teams-samples/tree/main/samples/meetings-share-to-stage-signing/csharp) | NA |

> [!NOTE]
>
> * Há suporte para aplicativos de reunião (painel lateral e estágio de reunião) no cliente da área de trabalho do Teams.
> * Os aplicativos de reunião (painel lateral e estágio de reunião) no cliente Web do Teams só têm suporte quando a visualização [do desenvolvedor está habilitada](/microsoftteams/platform/resources/dev-preview/developer-preview-intro#enable-developer-preview).

## <a name="step-by-step-guides"></a>Guias passo a passo

* Siga o [guia passo a passo](../sbs-meeting-token-generator.yml) para gerar o token de reunião em sua reunião do Teams.
* Siga o [guia passo a passo para gerar](../sbs-meetings-sidepanel.yml) o painel do lado da reunião em sua reunião do Teams.
* Siga o [guia passo a passo](../sbs-meetings-stage-view.yml) para compartilhar o modo de exibição do estágio de reunião em sua reunião do Teams.
* Siga o [guia passo a passo para](../sbs-meeting-content-bubble.yml) gerar uma notificação na reunião em sua reunião do Teams.

## <a name="see-also"></a>Confira também

* [Diretrizes de design de notificação na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Fluxo de autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Diretrizes de design da experiência de estágio de reunião compartilhada](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Adicionar aplicativos a reuniões por meio do Microsoft Graph](/graph/api/chat-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true)
