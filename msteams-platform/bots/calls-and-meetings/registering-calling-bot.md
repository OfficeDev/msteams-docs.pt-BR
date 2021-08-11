---
title: Registrar chamadas e reuniões bot para Microsoft Teams
description: Saiba como registrar um novo bot de chamada de áudio/vídeo para Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: chamando mídia de vídeo de áudio/vídeo de bot
ms.openlocfilehash: 5013ebcbce0bc94199e846f20fc6ee52238d302f1dd1b05872245ef2c6e32d91
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57709563"
---
# <a name="register-calls-and-meetings-bot-for-microsoft-teams"></a>Registrar chamadas e reuniões bot para Microsoft Teams

Um bot que participa de chamadas de áudio ou vídeo e reuniões online é um bot Microsoft Teams com os seguintes recursos extras usados para registrar o bot:

* Há uma nova versão do manifesto do aplicativo Teams com duas configurações adicionais `supportsCalling` e `supportsVideo` . Essas configurações estão incluídas na versão de [visualização](../../resources/dev-preview/developer-preview-intro.md) do desenvolvedor do manifesto Teams aplicativo.
* [As Graph microsoft](./registering-calling-bot.md#add-graph-permissions) devem ser configuradas para a ID do aplicativo Microsoft do bot.
* As Graph de chamadas e apIs de reuniões online exigem o consentimento do administrador de locatários.

## <a name="new-manifest-settings"></a>Novas configurações de manifesto

Os bots de chamadas e reuniões online têm as duas configurações adicionais a seguir no manifest.jsque habilitam áudio ou vídeo para seu bot Teams.

* `bots[0].supportsCalling`. Se presente e definido como `true` , Teams permite que seu bot participe de chamadas e reuniões online.
* `bots[0].supportsVideo`. Se presente e definido como `true` , Teams que seu bot oferece suporte a vídeo.

Se você quiser que seu IDE valide corretamente o manifest.jsno esquema para suas chamadas e reuniões bot para esses valores, você pode alterar o `$schema` atributo da seguinte maneira:

```json
"$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
```

A próxima seção permite que você crie um novo bot ou adicione recursos de chamada ao bot existente.

## <a name="create-new-bot-or-add-calling-capabilities"></a>Criar novo bot ou adicionar recursos de chamada

Para obter informações sobre como criar bots, [consulte create a bot for Teams](../how-to/create-a-bot-for-teams.md).

**Para criar um novo bot para Teams**

1. Use este link para criar um novo bot, `https://dev.botframework.com/bots/new` . Como alternativa, se você selecionar o botão Criar um **bot** no portal da Estrutura de Bots, crie seu bot no Microsoft Azure, para o qual você deve ter uma conta do Azure.
1. Adicione o Teams canal.
1. Selecione a **guia Chamar** na página Teams canal. Selecione **Habilitar** chamada e atualize **Webhook (para chamadas)** com sua URL HTTPS onde você recebe notificações de entrada, por exemplo `https://contoso.com/teamsapp/api/calling` . Para obter mais informações, consulte [configuring channels](/bot-framework/portal-configure-channels).

    ![Configurar Teams de canal](~/assets/images/calls-and-meetings/configure-msteams-channel.png)

A próxima seção fornece uma lista de permissões de aplicativo com suporte para chamadas e reuniões online.

## <a name="add-graph-permissions"></a>Adicionar Graph permissões

O Graph fornece permissões granulares para controlar o acesso que os aplicativos têm aos recursos. Você decide quais permissões para Graph suas solicitações de aplicativo. As Graph de chamada de APIs suportam permissões de aplicativo, que são usadas por aplicativos que são executados sem um usuário in-loco presente. Um administrador de locatário deve conceder consentimento às permissões do aplicativo.

### <a name="application-permissions-for-calls"></a>Permissões de aplicativo para chamadas

A tabela a seguir fornece uma lista de permissões de aplicativo para chamadas:

|Permissão    |Exibir cadeia de caracteres   |Descrição |Consentimento do administrador necessário |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| Calls.Initiate.All |Inicie chamadas de saída 1:1 da visualização do aplicativo. |Permite que o aplicativo faça chamadas de saída para um único usuário e transfira chamadas para usuários no diretório da sua organização, sem um usuário conectado.|Sim|
| Calls.InitiateGroupCall.All |Inicie chamadas de grupo de saída da visualização do aplicativo. |Permite que o aplicativo faça chamadas para vários usuários e adicione participantes a reuniões em sua organização, sem um usuário conectado.|Sim|
| Calls.JoinGroupCall.All |Participe de chamadas de grupo e reuniões como uma visualização de aplicativo. |Permite que o aplicativo ingresse em reuniões agendadas e chamadas de grupo em sua organização, sem um usuário conectado. O aplicativo é ingressado com os privilégios de um usuário de diretório para reuniões em seu locatário.|Sim|
| Calls.JoinGroupCallasGuest.All |Participe de chamadas de grupo e reuniões como uma visualização de convidados. |Permite que o aplicativo ingresse anonimamente no grupo chamadas e em reuniões agendadas em sua organização, sem um usuário conectado. O aplicativo é ingressado como convidado para reuniões em seu locatário.|Sim|
| Calls.AccessMedia.All |Acessar fluxos de mídia em uma chamada como uma visualização de aplicativo. |Permite que o aplicativo obtenha acesso direto aos fluxos de mídia em uma chamada sem um usuário conectado.|Sim|

> [!IMPORTANT]
> Você não pode usar a API do Media Access para gravar ou persistir conteúdo de mídia de chamadas ou reuniões que seu aplicativo acessa ou derivar dados desse registro ou gravação de conteúdo de mídia. Primeiro, você deve chamar a [ `updateRecordingStatus` API](/graph/api/call-updaterecordingstatus) para indicar que a gravação foi iniciada e receber uma resposta de sucesso dessa API. Se o aplicativo começar a gravar qualquer reunião ou chamada, ele deve encerrar a gravação antes de chamar a API para indicar que a `updateRecordingStatus` gravação terminou.

### <a name="application-permissions-for-online-meetings"></a>Permissões de aplicativo para reuniões online

A tabela a seguir fornece uma lista de permissões de aplicativo para reuniões online:

|Permissão    |Exibir cadeia de caracteres   |Descrição |Consentimento do administrador necessário |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| OnlineMeetings.Read.All |Ler detalhes da reunião online na visualização do aplicativo|Permite que o aplicativo leia os detalhes da reunião online em sua organização, sem um usuário in-locar.|Sim|
| OnlineMeetings.ReadWrite.All |Ler e criar reuniões online na visualização do aplicativo em nome de um usuário|Permite que o aplicativo crie reuniões online em sua organização em nome de um usuário, sem um usuário de acesso.|Sim|

### <a name="assign-permissions"></a>Atribuir permissões

Você deve configurar as permissões de aplicativo para seu bot antecipadamente usando o [portal do Azure](https://aka.ms/aadapplist) se preferir usar o ponto de extremidade [Azure Active Directory (AAD) V1](/azure/active-directory/develop/azure-ad-endpoint-comparison).

### <a name="get-tenant-administrator-consent"></a>Obter consentimento do administrador de locatários

Para aplicativos que usam o ponto de extremidade do AAD V1, um administrador de locatários pode consentir com as permissões do aplicativo usando o portal do [Azure](https://portal.azure.com) quando seu aplicativo estiver instalado em sua organização. Como alternativa, você pode fornecer uma experiência de assinatura em seu aplicativo por meio do qual os administradores podem consentir com as permissões configuradas. Depois que o consentimento do administrador é registrado pelo AAD, seu aplicativo pode solicitar tokens sem precisar solicitar consentimento novamente.

Você pode contar com um administrador para conceder as permissões que seu aplicativo precisa no [portal do Azure.](https://portal.azure.com) Uma opção melhor é fornecer uma experiência de assinatura para administradores usando o ponto de extremidade do AAD `/adminconsent` V2. Para obter mais informações, consulte [instruções sobre como construir uma URL de consentimento do administrador.](https://developer.microsoft.com/graph/docs/concepts/auth_v2_service#3-get-administrator-consent)

> [!NOTE]
> Para construir a URL de consentimento do administrador do locatário, é necessário um URI de redirecionamento configurado ou URL de resposta no portal de [registro do aplicativo.](https://apps.dev.microsoft.com/) Para adicionar URLs de resposta para seu bot, acesse seu registro de bot, escolha **Opções Avançadas**  >  **Editar Manifesto do Aplicativo.** Adicione sua URL de redirecionamento à `replyUrls` coleção.

> [!IMPORTANT]
> Sempre que você fizer uma alteração nas permissões do aplicativo, também deverá repetir o processo de consentimento do administrador. As alterações feitas no portal de registro do aplicativo não serão refletidas até que o consentimento tenha sido reaplicado pelo administrador do locatário.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Notificações de chamadas recebidas](~/bots/calls-and-meetings/call-notifications.md)
