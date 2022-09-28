---
title: Registrar chamadas e reuniões do bot do Microsoft Teams
description: Saiba como registrar um novo bot de chamada de áudio/vídeo para o Microsoft Teams, criar um bot ou adicionar funcionalidade de chamada, adicionar permissões de grafo. Exemplo para criar chamada, ingressar na reunião e transferir chamada.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 2563d94e944a7d4058d1417be2f3816e3f565bff
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100921"
---
# <a name="register-calls-and-meetings-bot-for-microsoft-teams"></a>Registrar chamadas e reuniões do bot do Microsoft Teams

Um bot que participa de chamadas de áudio ou vídeo e de reuniões online é um bot regular do Microsoft Teams com os seguintes recursos extras usados ​​para registrar o bot:

* Há uma nova versão do manifesto de aplicativo Teams com duas configurações adicionais, `supportsCalling` e `supportsVideo`. Essas configurações estão incluídas no [esquema de manifesto do Microsoft Teams](../../resources/schema/manifest-schema.md).
* [As permissões do Microsoft Graph](./registering-calling-bot.md#add-graph-permissions) devem ser configuradas para a ID do Aplicativo Microsoft do bot.
* As permissões de chamadas do Graph e APIs de reuniões online exigem o consentimento do administrador do locatário.

## <a name="new-manifest-settings"></a>Novas configurações de manifesto

Os bots de chamadas e reuniões online têm as duas configurações adicionais a seguir no manifest.json que habilitam áudio ou vídeo para o bot no Teams.

* `bots[0].supportsCalling`. If present and set to `true`, Teams allows your bot to participate in calls and online meetings.
* `bots[0].supportsVideo`. If present and set to `true`, Teams knows that your bot supports video.

Se quiser que o IDE valide corretamente o esquema manifest.json para suas chamadas e o bot de reuniões para esses valores, você pode alterar o atributo `$schema` da seguinte maneira:

```json
"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
```

A próxima seção permite que você crie um novo bot ou adicione recursos de chamada ao bot existente.

## <a name="create-new-bot-or-add-calling-capabilities"></a>Criar um bot ou adicionar recursos de chamada

Para obter informações sobre como criar bots, confira [criar um bot para o Teams](../how-to/create-a-bot-for-teams.md).

Para criar um novo bot para o Teams:

1. Use this link to create a new bot, `https://dev.botframework.com/bots/new`. Alternately, if you select the **Create a bot** button in the Bot Framework portal, you create your bot in Microsoft Azure, for which you must have an Azure account.
1. Adicione o canal do Teams.
1. Selecione a guia **Chamada** na página do canal do Teams. Selecione **Habilitar chamada** e, em seguida, atualize **Webhook (para chamada)** com a URL HTTPS em que você recebe notificações de entrada, por exemplo `https://contoso.com/teamsapp/api/calling`. Para obter mais informações, confira [configuração de canais](/bot-framework/portal-configure-channels).

    ![Configurar informações do canal do Teams](~/assets/images/calls-and-meetings/configure-msteams-channel.png)

A próxima seção fornece uma lista de permissões de aplicativo com suporte para chamadas e reuniões online.

## <a name="add-graph-permissions"></a>Adicionar permissões do Graph

O Graph fornece permissões granulares para controlar o acesso que os aplicativos têm aos recursos. Como desenvolvedor, você decide quais permissões seu aplicativo deverá solicitar para o Microsoft Graph. As APIs de chamada do Graph dão suporte a permissões de aplicativo, que são usadas por aplicativos executados sem um usuário conectado presente. Um administrador de locatários deve dar consentimento a permissões de aplicativo.

### <a name="application-permissions-for-calls"></a>Permissões de aplicativo para chamadas

A tabela a seguir fornece uma lista de permissões de aplicativo para chamadas:

|Permissão    |Sequência de exibição   |Descrição |É necessário o consentimento do administrador |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| Calls.Initiate.All |Inicie chamadas individuais de saída a partir da visualização do aplicativo. |Permite que o aplicativo faça chamadas de saída para um único usuário e transfira chamadas para usuários no diretório da sua organização, sem um usuário conectado.|Sim|
| Calls.InitiateGroupCall.All |Inicie as chamadas de saída 1:1 e de grupo na visualização do aplicativo. |Permite que o aplicativo coloque chamadas de saída para um único usuário, vários usuários, transfira chamadas e adicione participantes a reuniões em sua organização, sem um usuário conectado.|Sim|
| Calls.JoinGroupCall.All |Ingresse em chamadas em grupo e reuniões como uma visualização de aplicativo. |Permite que o aplicativo ingresse em reuniões agendadas e chamadas de grupo em sua organização, sem um usuário conectado. O aplicativo será associado aos privilégios de um usuário do diretório para reuniões em seu locatário.|Sim|
| Calls.JoinGroupCallasGuest.All |Ingresse em chamadas em grupo e reuniões como uma visualização de convidado. |Permite que o aplicativo ingresse anonimamente no grupo chamadas e em reuniões agendadas em sua organização, sem um usuário conectado. O aplicativo ingressará como convidado para reuniões em seu locatário.|Sim|
| Calls.AccessMedia.All |Acessar fluxos de mídia em uma chamada como uma visualização de aplicativo. |Permite que o aplicativo obtenha acesso direto aos fluxos de mídia em uma chamada sem um usuário conectado.|Sim|

> [!IMPORTANT]
> Não é possível usar a API de Acesso à Mídia para gravar ou persistir conteúdo de mídia de chamadas ou reuniões que seu aplicativo acessa ou deriva dados desse registro ou gravação de conteúdo de mídia. Primeiro, você deve chamar a [`updateRecordingStatus` API](/graph/api/call-updaterecordingstatus) para indicar que a gravação começou e receber uma resposta bem-sucedida dessa API. Se o aplicativo começar a gravar qualquer reunião ou chamada, ele deverá encerrar a gravação antes de chamar a API `updateRecordingStatus` para indicar que a gravação foi encerrada.

### <a name="application-permissions-for-online-meetings"></a>Permissões de aplicativo para reuniões online

A tabela a seguir fornece uma lista de permissões de aplicativo para reuniões online:

|Permissão    |Sequência de exibição   |Descrição |É necessário o consentimento do administrador |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| OnlineMeetings.Read.All |Ler detalhes da reunião online na visualização do aplicativo|Permite que o aplicativo leia os detalhes da reunião online em sua organização, sem um usuário conectado.|Sim|
| OnlineMeetings.ReadWrite.All |Ler e criar reuniões online na visualização do aplicativo em nome de um usuário|Permite que o aplicativo crie reuniões online em sua organização em nome de um usuário, sem um usuário conectado.|Sim|

### <a name="assign-permissions"></a>Atribuir permissões

Você deve configurar as permissões de aplicativo para o bot com antecedência usando o [portal do Microsoft Azure](https://portal.azure.com) se preferir usar o [ponto de extremidade do Microsoft Azure Active Directory (Azure AD) V1](/azure/active-directory/develop/azure-ad-endpoint-comparison).

### <a name="get-tenant-administrator-consent"></a>Obter consentimento do administrador de locatários

For apps using the Azure AD V1 endpoint, a tenant administrator can consent to the application permissions using the [Microsoft Azure portal](https://portal.azure.com) when your app is installed in their organization. Alternately, you can provide a sign-up experience in your app through which administrators can consent to the permissions you configured. Once administrator consent is recorded by Azure AD, your app can request tokens without having to request consent again.

You can rely on an administrator to grant the permissions your app needs at the [Microsoft Azure portal](https://portal.azure.com). A better option is to provide a sign-up experience for administrators by using the Azure AD V2 `/adminconsent` endpoint. For more information, see [instructions on constructing an Admin consent URL](/graph/auth-v2-service#3-get-administrator-consent).

> [!NOTE]
> Para construir a URL de consentimento do administrador do locatário, será necessário um URI de redirecionamento configurado ou uma URL de resposta no [portal de registro do aplicativo](https://apps.dev.microsoft.com/). Para adicionar URLs de resposta para seu bot, acesse o registro do bot, escolha **Opções Avançadas** > **Editar Manifesto do Aplicativo**. Adicione a URL de redirecionamento à coleção `replyUrls`.

> [!IMPORTANT]
> Sempre que fizer uma alteração nas permissões configuradas, repita também o processo de consentimento do administrador. As alterações feitas no portal de registro do aplicativo não serão refletidas até que o consentimento seja reaplicado pelo administrador do locatário.

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Graph** |
|---------------|----------|--------|
| Bot de chamada e reunião | O aplicativo de amostra demonstra como o Bot pode criar chamadas, ingressar na reunião e transferir chamadas. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-calling-meeting/csharp) |

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo](../../sbs-calling-and-meeting.yml) para configurar a chamada e a reunião em um bot.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Notificações de chamadas recebidas](~/bots/calls-and-meetings/call-notifications.md)

## <a name="see-also"></a>Confira também

* [Notificações de chamadas recebidas](~/bots/calls-and-meetings/call-notifications.md)
* [Como desenvolver bots de chamadas e reuniões online em seu computador local](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
* [Exibir permissões do aplicativo e conceder consentimento do administrador](/MicrosoftTeams/app-permissions-admin-center)
