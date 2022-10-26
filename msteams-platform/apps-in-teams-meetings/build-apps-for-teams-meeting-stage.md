---
title: Criar aplicativos para o estágio de reunião do Teams
author: v-sdhakshina
description: Saiba como criar aplicativos para o estágio de reunião do Teams, compartilhar para as APIs de estágio e gerar um link profundo para compartilhar conteúdo para o estágio em reuniões.
ms.topic: conceptual
ms.author: v-sdhakshina
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: 48834addceb0e7a6e4522c096cf40b117312647c
ms.sourcegitcommit: 372aade09e62ac7e5936215173a6632fbb042c9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2022
ms.locfileid: "68699133"
---
# <a name="build-apps-for-teams-meeting-stage"></a>Criar aplicativos para o estágio de reunião do Teams

O compartilhamento no estágio permite que os usuários compartilhem um aplicativo para o estágio de reunião do painel do lado da reunião em uma reunião em andamento. Esse compartilhamento é interativo e colaborativo em comparação ao compartilhamento passivo de tela.

Para invocar o compartilhamento para o estágio, os usuários podem selecionar o ícone **Compartilhar para Estágio** no lado superior direito do painel lateral da reunião. **O ícone Compartilhar para Estágio** é nativo do cliente do Teams e selecioná-lo compartilha todo o aplicativo para o estágio de reunião.

## <a name="app-manifest-settings-for-apps-in-meeting-stage"></a>Configurações de manifesto de aplicativo para aplicativos em estágio de reunião

Para compartilhar um aplicativo na fase de reunião, atualize a `context` propriedade no manifesto do aplicativo da seguinte maneira:

```json
"context":[ 
    "meetingSidePanel", 
    "meetingStage" 
     ] 
```

## <a name="advanced-share-to-stage-apis"></a>Compartilhamento avançado para APIs de estágio

Há muitos cenários em que o compartilhamento de todo o aplicativo para o estágio de reunião não é tão útil quanto compartilhar partes específicas do aplicativo:  

1. Para um aplicativo de brainstorming ou whiteboard, um usuário pode querer compartilhar um quadro específico em uma reunião versus todo o aplicativo com todos os quadros.  

1. Para um aplicativo médico, um médico pode querer compartilhar apenas o Raio-X na tela com o paciente versus compartilhar todo o aplicativo com todos os registros ou resultados dos pacientes e assim por diante.

1. Um usuário pode querer compartilhar conteúdo de um único provedor de conteúdo por vez (por exemplo, YouTube) em vez de compartilhar um catálogo de vídeo inteiro no palco.

Para ajudar os usuários nesses cenários, lançamos APIs no SDK do Cliente do Teams que permitem que você invoque programaticamente o compartilhamento para o estágio para partes específicas do aplicativo a partir de um botão no painel lateral da reunião.

:::image type="content" source="../assets/images/apps-in-meetings/shared-meeting-stage-edit-review-component.png" alt-text="A captura de tela mostra o modo de exibição do estágio de reunião do compartilhamento.":::

Use as seguintes APIs para compartilhar parte específica do aplicativo:

|Método| Descrição| Source|
|---|---|----|
|[**Compartilhar Conteúdo do Aplicativo na Janela de Conteúdo Compartilhado**](#share-app-content-to-stage-api)| Compartilhe partes específicas do aplicativo para o estágio de reunião do painel do lado da reunião em uma reunião. | [SDK da biblioteca JavaScript do Microsoft Teams](/javascript/api/@microsoft/teams-js/meeting) |
|[**Obter Estado de Compartilhamento da Janela de Conteúdo**](#get-app-content-stage-sharing-state-api)| Busque informações sobre o estado de compartilhamento do aplicativo no estágio da reunião. | [SDK da biblioteca JavaScript do Microsoft Teams](/javascript/api/@microsoft/teams-js/meeting.iappcontentstagesharingstate) |
|[**Obter Recursos de Compartilhamento da Janela de Conteúdo**](#get-app-content-stage-sharing-capabilities-api)| Busque os recursos do aplicativo para compartilhar com o estágio da reunião. | [SDK da biblioteca JavaScript do Microsoft Teams](/javascript/api/@microsoft/teams-js/meeting.iappcontentstagesharingcapabilities) |

## <a name="share-app-content-to-stage-api"></a>Compartilhar conteúdo do aplicativo para preparar a API

A API `shareAppContentToStage` permite que você compartilhe partes específicas do seu aplicativo no estágio da reunião. A API está disponível por meio do SDK do cliente do Teams.

### <a name="prerequisite"></a>Pré-requisito

* Para usar a API `shareAppContentToStage`, você deve obter as permissões de RSC. No manifesto do aplicativo, configure a propriedade `authorization`, e `name` e `type` no campo `resourceSpecific`. Por exemplo:

    ```json
    "authorization": {
        "permissions": { 
        "resourceSpecific": [
        { 
         "name": "MeetingStage.Write.Chat",
         "type": "Delegated"
        }
        ]
    }
    }
    ```

* `appContentUrl` deve ser permitido por `validDomains` matriz dentro de manifest.json, caso contrário, a API retorna um erro 501.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui os parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError* ou nulo quando o compartilhamento for bem-sucedido. O *resultado* pode conter um valor verdadeiro, se houver um compartilhamento bem-sucedido ou nulo quando o compartilhamento falhar. |
|**appContentURL**| Cadeia de caracteres | Sim | A URL que será compartilhada no estágio. |

### <a name="example"></a>Exemplo

```javascript
const appContentUrl = "https://www.bing.com/";

microsoftTeams.meeting.shareAppContentToStage((err, result) => {
    if (result) {
        // handle success
    }
    if (err) {
        // handle error
    }
}, appContentUrl);
```

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1.000** | O aplicativo não tem permissões adequadas para permitir que o compartilhamento seja estágio.|

## <a name="get-app-content-stage-sharing-state-api"></a>Obter API de estado de compartilhamento do estágio de conteúdo do aplicativo

A `getAppContentStageSharingState` API permite buscar informações sobre o compartilhamento de aplicativos no estágio de reunião.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError*, no caso de um erro, ou nulo quando o compartilhamento for bem-sucedido. O *resultado* pode conter um `IAppContentStageSharingState` objeto, quando o compartilhamento for bem-sucedido ou nulo, em caso de erro.|

### <a name="example"></a>Exemplo

```javascript
microsoftTeams.meeting.getAppContentStageSharingState((err, result) => {
    if (result.isAppSharing) {
        // Indicates if app is sharing content on the meeting stage.
    }
});
```

O corpo da resposta JSON para `getAppContentStageSharingState` API é:

```json
{
   "isAppSharing":true
} 
```

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1.000** | O aplicativo não tem permissões adequadas para permitir que o compartilhamento seja estágio.|

## <a name="get-app-content-stage-sharing-capabilities-api"></a>Obter a API de recursos de compartilhamento do estágio de conteúdo do aplicativo

A API `getAppContentStageSharingCapabilities` permite que você busque os recursos do aplicativo para compartilhamento no estágio de reunião.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError* ou nulo quando o compartilhamento for bem-sucedido. O resultado pode conter um `IAppContentStageSharingCapabilities` objeto, quando o compartilhamento for bem-sucedido ou nulo, em caso de erro.|

### <a name="example"></a>Exemplo

```javascript
microsoftTeams.meeting.getAppContentStageSharingCapabilities((err, result) => {
    if (result.doesAppHaveSharePermission) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
```

O corpo da resposta JSON para `getAppContentStageSharingCapabilities` API é:

```json
{
   "doesAppHaveSharePermission":true
} 
```

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1.000** | O aplicativo não tem permissões para permitir que o compartilhamento seja estágio.|

## <a name="generate-a-deep-link-to-share-content-to-stage-in-meetings"></a>Gerar um link profundo para compartilhar conteúdo para o estágio em reuniões

Você também pode gerar um link profundo para compartilhar o aplicativo para o estágio e iniciar ou ingressar em uma reunião.

> [!NOTE]
>
> * Atualmente, o link profundo para compartilhar conteúdo para o estágio em reuniões está passando por melhorias de UX e está disponível apenas na [versão prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).
> * O link profundo para compartilhar conteúdo para o estágio na reunião tem suporte somente no cliente da área de trabalho do Teams.

Quando um link profundo é selecionado em um aplicativo por um usuário que faz parte de uma reunião em andamento, o aplicativo é compartilhado no palco e uma janela pop-up de permissão é exibida. Os usuários podem conceder acesso aos participantes para colaborar com um aplicativo.

:::image type="content" source="../assets/images/intergrate-with-teams/screenshot-of-pop-up-permission.png" alt-text="A captura de tela é um exemplo que mostra uma janela pop-up de permissão.":::

Quando um usuário não está em uma reunião, o usuário é redirecionado para o calendário do Teams, onde pode participar de uma reunião ou iniciar uma reunião instantânea (Atender agora).

:::image type="content" source="../assets/images/intergrate-with-teams/Instant-meetnow-pop-up.png" alt-text="A captura de tela é um exemplo que mostra uma janela pop-up quando não há uma reunião em andamento.":::

Depois que o usuário inicia uma reunião instantânea (Atender agora), ele pode adicionar participantes e interagir com o aplicativo.

:::image type="content" source="../assets/images/intergrate-with-teams/Screenshot-ofmeet-now-option-pop-up.png" alt-text="A captura de tela é um exemplo que mostra uma opção para adicionar participantes e como interagir com o aplicativo.":::

Para adicionar um link profundo para compartilhar conteúdo no palco, você precisa ter um contexto de aplicativo. O contexto do aplicativo permite que o cliente do Teams busque o manifesto do aplicativo e verifique se o compartilhamento no palco é possível. A seguir está um exemplo de um contexto de aplicativo.

`{ "appSharingUrl" : "https://teams.microsoft.com/extensibility-apps/meetingapis/view", "appId": "9ec80a73-1d41-4bcb-8190-4b9eA9e29fbb" , "useMeetNow": false }`

Os parâmetros de consulta para o contexto do aplicativo são:

* `appID`: esta é a ID que pode ser obtida do manifesto do aplicativo.
* `appSharingUrl`: a URL que precisa ser compartilhada no palco deve ser um domínio válido definido no manifesto do aplicativo. Se a URL não for um domínio válido, uma caixa de diálogo de erro aparecerá para fornecer ao usuário uma descrição do erro.
* `useMeetNow`: isso inclui um parâmetro booliano que pode ser verdadeiro ou falso.
  * **True**: quando o `UseMeetNow` valor for verdadeiro e se não houver uma reunião em andamento, uma nova reunião do Meet now será iniciada. Quando houver uma reunião em andamento, esse valor será ignorado.

  * **False**: o valor padrão de `UseMeetNow` é falso, o que significa que quando um link profundo é compartilhado para o palco e não há uma reunião em andamento, um pop-up de calendário será exibido. No entanto, você pode compartilhar diretamente durante uma reunião.

Verifique se todos os parâmetros de consulta estão codificados corretamente no URI e que o contexto do aplicativo precisa ser codificado duas vezes na URL final. A seguir está um exemplo.

```json
var appContext= JSON.stringify({ "appSharingUrl" : "https://teams.microsoft.com/extensibility-apps/meetingapis/view", "appId": "9cc80a93-1d41-4bcb-8170-4b9ec9e29fbb", "useMeetNow":false })
var encodedContext = encodeURIComponent(appcontext).replace(/'/g,"%27").replace(/"/g,"%22")
var encodedAppContext = encodeURIComponent(encodedContext).replace(/'/g,"%27").replace(/"/g,"%22")
```

Um link profundo pode ser iniciado na Web do Teams ou no cliente da área de trabalho do Teams.

* **Teams Web**: use o seguinte formato para iniciar um link profundo da Web do Teams para compartilhar conteúdo no palco.

    `https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`

    Exemplo: `https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`

    |Link profundo|Formatar|Exemplo|
    |---------|---------|---------|
    |Para compartilhar o aplicativo e abrir o calendário do Teams, quando UseMeeetNow for **false**, padrão.|`https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`|`https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Afalse%257D`|
    |Para compartilhar o aplicativo e iniciar uma reunião instantânea, quando UseMeeetNow for **true**.|`https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`|`https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`|

* **Cliente da área de trabalho da equipe**: use o seguinte formato para iniciar um link profundo do cliente da área de trabalho do Teams para compartilhar conteúdo no palco.

    `msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`

    Exemplo: `msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`

    |Link profundo|Formatar|Exemplo|
    |---------|---------|---------|
    |Para compartilhar o aplicativo e abrir o calendário do Teams, quando UseMeeetNow for **false**, padrão.|`msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`|`msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Afalse%257D`|
    |Para compartilhar o aplicativo e iniciar uma reunião instantânea, quando UseMeeetNow for **true**.|`msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`|`msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`|

Os parâmetros de consulta são:

* `deepLinkId`: qualquer identificador usado para correlação de telemetria.
* `fqdn`: `fqdn` é um parâmetro opcional, que pode ser usado para alternar para um ambiente apropriado de uma reunião para compartilhar um aplicativo no palco. Ele dá suporte a cenários em que um compartilhamento de aplicativo específico acontece em um determinado ambiente. O valor padrão de `fqdn` é a URL corporativa e os valores possíveis são `Teams.live.com` para o Teams for Life, `teams.microsoft.com`ou `teams.microsoft.us`.

Para compartilhar todo o aplicativo para o estágio, no manifesto do aplicativo, você deve configurar `meetingStage` e `meetingSidePanel` como contextos de quadro, consulte [manifesto do aplicativo](../resources/schema/manifest-schema.md). Caso contrário, os participantes da reunião podem não poder ver o conteúdo no palco.

> [!NOTE]
> Para que seu aplicativo passe a validação, ao criar um link profundo do seu site, aplicativo Web ou Cartão Adaptável, use **Compartilhar na reunião** como cadeia de caracteres ou cópia.

## <a name="build-an-in-meeting-document-signing-app"></a>Criar um aplicativo de assinatura de documento em reunião

Você pode criar um aplicativo em reunião para permitir que os participantes da reunião assinem documentos em tempo real. Ele facilita a revisão e a assinatura de documentos em uma única sessão. Os participantes podem assinar os documentos usando sua identidade de locatário atual.

Você pode usar um aplicativo de assinatura na reunião para:

- Adicionar documentos a serem revisados durante uma reunião
- Compartilhar documentos a serem revisados para o estágio principal
- Assinar documentos usando a identidade do signatário

Os participantes podem examinar e assinar documentos, como contratos de compra e pedidos de compra.

![aplicativo de assinatura de documentos na reunião](~/assets//images/sbs-inmeeting-doc-signing/signing-clip.gif)

As seguintes funções participantes podem estar envolvidas durante a reunião:

- **Criador de documentos**: essa função pode adicionar seus próprios documentos a serem revisados e assinados.
- **Signatário**: essa função pode assinar documentos revisados.
- **Leitor**: essa função pode exibir os documentos adicionados à reunião.

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|----------------|
|Exemplo de estágio de reunião | Aplicativo de exemplo para mostrar uma guia no estágio de reunião para colaboração | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
| Notificação na reunião | Demonstra como implementar a notificação em reunião usando o bot. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs) |
| Assinatura de documento em reunião | Demonstra como implementar um aplicativo de assinatura de documentos do Teams. Inclui o compartilhamento de conteúdo de aplicativo específico para o estágio, o SSO do Teams e a exibição de estágio específica do usuário. | [Exibir](https://github.com/officedev/microsoft-teams-samples/tree/main/samples/meetings-share-to-stage-signing/csharp) | NA |

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo](../sbs-inmeeting-document-signing.yml) para criar um aplicativo de assinatura de documentos em reunião.

## <a name="see-also"></a>Confira também

* [Fluxo de autenticação de equipes para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para reuniões do Teams](teams-apps-in-meetings.md)
* [Criar guias para reunião](build-tabs-for-meeting.md)
* [Criar conversa extensível para chat de reunião](build-extensible-conversation-for-meeting-chat.md)
* [Criar aplicativos para usuários anônimos](build-apps-for-anonymous-user.md)
* [APIs de reunião avançadas](meeting-apps-apis.md)
* [Cenas personalizadas do Modo Conferência](~/apps-in-teams-meetings/teams-together-mode.md)
* [SDK do Live Share](teams-live-share-overview.md)
* [Guia passo a passo para criar um aplicativo de assinatura de documentos em reunião](../sbs-inmeeting-document-signing.yml)
