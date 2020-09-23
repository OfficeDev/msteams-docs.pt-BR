---
title: Registrando um bot de chamada e reunião para o Microsoft Teams
description: Saiba como registrar um novo bot de chamada de áudio/vídeo para o Microsoft Teams
keywords: áudio do bot de chamada mídia de vídeo de áudio/vídeo
ms.openlocfilehash: 4db6c29352aa117e0dd1959826d0560359864d8a
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48209750"
---
# <a name="register-a-calling-bot-for-microsoft-teams"></a>Registrar um bot de chamada para o Microsoft Teams

Um bot que participa de chamadas de áudio/vídeo e reuniões online é um simples bot do Microsoft Teams com alguns recursos adicionais:

* Há uma nova versão do manifesto de aplicativo do teams com duas configurações adicionais `supportsCalling` e `supportsVideo` . Essas configurações estão incluídas na versão de [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) do manifesto do aplicativo Microsoft Teams.
* [As permissões do Microsoft Graph](./registering-calling-bot.md#add-microsoft-graph-permissions) devem ser configuradas para a ID do aplicativo da Microsoft de seu bot.
* As chamadas do Microsoft Graph e as permissões de APIs de reuniões online exigem o consentimento do administrador do locatário.

Vamos discutir o acima mais detalhadamente.

## <a name="new-manifest-settings"></a>Novas configurações de manifesto

Os bots de chamadas e de reuniões online têm duas configurações adicionais no manifest.jsque permitem áudio/vídeo para o bot no Microsoft Teams.

* `bots[0].supportsCalling`. Se presente e definido como `true` , o Microsoft Teams permitirá que o bot participe de chamadas e reuniões online.
* `bots[0].supportsVideo`. Se presente e definido como `true` , o Teams sabe que seu bot oferece suporte a vídeo.

Se quiser que o IDE valide corretamente o manifest.jsno esquema para o seu bot de chamada e de reunião para estes valores, você pode alterar o `$schema` atributo da seguinte maneira:

```json
"$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
```

## <a name="creating-a-new-bot-or-adding-calling-capabilities-to-an-existing-bot"></a>Criando um novo bot ou adicionando recursos de chamada a um bot existente

A criação de um novo bot é abordada em mais detalhes no tópico [criar um bot para o Microsoft Teams](../how-to/create-a-bot-for-teams.md) , mas repetiremos alguns deles:

1. Use este link para criar um novo bot: `https://dev.botframework.com/bots/new` . Se, em vez disso, você selecionar o botão *criar um bot* no portal da estrutura do bot, você criará seu bot no Microsoft Azure, para o qual você precisará de uma conta do Azure.
1. Adicione o canal do Microsoft Teams. Clique na guia "chamada" na página Microsoft Teams Channel e selecione **habilitar chamadas**e, em seguida, atualizar **webhook (para chamadas)** com a URL https onde você receberá notificações de entrada, por exemplo `https://contoso.com/teamsapp/api/calling` ,. Consulte [Configurando canais](/bot-framework/portal-configure-channels) para obter mais informações sobre como configurar canais.
  ![Configurar informações de canal do Microsoft Teams](~/assets/images/calls-and-meetings/configure-msteams-channel.png)

## <a name="add-microsoft-graph-permissions"></a>Adicionar permissões do Microsoft Graph

O Microsoft Graph expõe permissões granulares que controlam o acesso que os aplicativos têm aos recursos. Como desenvolvedor, você decide quais permissões para o Microsoft Graph seu aplicativo deverá solicitar.  As APIs de chamada do Microsoft Graph dão suporte a _permissões de aplicativo_, que são usadas por aplicativos executados sem um usuário conectado presente.  Um administrador de locatários deve conceder consentimento às permissões do aplicativo. Veja a seguir uma lista dessas permissões:

### <a name="application-permissions-calls"></a>Permissões de aplicativo: chamadas

|Permissão    |Exibir Cadeia de Caracteres   |Descrição |Consentimento Obrigatório do Administrador |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
|_Calls.Initiate.All_|Iniciar chamadas de saída 1:1 do aplicativo (visualização)|Permite que o aplicativo faça chamadas de saída para um único usuário e transfira chamadas para usuários no diretório da sua organização, sem um usuário conectado.|Sim|
|_Calls.InitiateGroupCall.All_|Iniciar a saída de chamadas de grupo do aplicativo (visualização)|Permite que o aplicativo faça chamadas para vários usuários e adicione participantes a reuniões em sua organização, sem um usuário conectado.|Sim|
|_Calls.JoinGroupCall.All_|Ingresse em reuniões e chamadas de grupo como um aplicativo (visualização)|Permite que o aplicativo ingresse em reuniões agendadas e chamadas de grupo em sua organização, sem um usuário conectado. O aplicativo será associado aos privilégios de um usuário do diretório para reuniões em seu locatário.|Sim|
|_Calls.JoinGroupCallasGuest.All_|Ingressar em reuniões e chamadas de grupo como um convidado (visualização)|Permite que o aplicativo ingresse anonimamente no grupo chamadas e em reuniões agendadas em sua organização, sem um usuário conectado. O aplicativo ingressará como convidado para reuniões em seu locatário.|Sim|
|_Calls. AccessMedia. All_ <sup> _Veja abaixo_</sup>|Acessar fluxos de mídia em uma chamada como um aplicativo (visualização)|Permite que o aplicativo obtenha acesso direto aos fluxos de mídia em uma chamada sem um usuário conectado.|Sim|

> [!IMPORTANT]
> Você **não pode** usar a API Microsoft. Graph. calls. Media para registrar ou manter o conteúdo de mídia de chamadas ou reuniões que seu bot acessa.

### <a name="application-permissions-online-meetings"></a>Permissões de aplicativo: reuniões online

|Permissão    |Exibir Cadeia de Caracteres   |Descrição |Consentimento Obrigatório do Administrador |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
|_OnlineMeetings.Read.All_|Ler detalhes de Reunião Online do aplicativo (visualização)|Permite que o aplicativo leia os detalhes da Reunião Online em sua organização, sem um usuário conectado.|Sim|
|_OnlineMeetings.ReadWrite.All_|Leia e crie reuniões Online do aplicativo (visualização) em nome de um usuário|Permite que o aplicativo crie reuniões Online em sua organização em nome de usuário, sem um usuário conectado.|Sim|

### <a name="assigning-permissions"></a>Atribuindo permissões

Você deve configurar as permissões de aplicativo para o bot com antecedência. Recomendamos o uso do [portal de registro de aplicativos da Microsoft](https://apps.dev.microsoft.com/) , conforme descrito [aqui](/graph/auth_register_app_v2) , porque o seu bot foi configurado; no entanto, você ainda pode usar o [portal do Azure](https://aka.ms/aadapplist) se preferir usar o [ponto de extremidade do Azure ad v1](/azure/active-directory/develop/azure-ad-endpoint-comparison).

### <a name="getting-tenant-administrator-consent"></a>Obtendo consentimento do administrador de locatários

Para aplicativos que usam o ponto de extremidade do Azure AD v1, um administrador de locatários pode consentir as permissões de aplicativo usando o [portal do Azure](https://portal.azure.com) quando o aplicativo é instalado em sua organização ou você pode fornecer uma experiência de inscrição no seu aplicativo através da qual os administradores podem consentir as permissões que você configurou. Depois que o consentimento do administrador é registrado pelo Azure AD, seu aplicativo pode solicitar tokens sem precisar solicitar o consentimento novamente.

Você pode confiar em um administrador para conceder as permissões de que seu aplicativo precisa no [portal do Azure](https://portal.azure.com); no entanto, geralmente, uma opção melhor é fornecer uma experiência de inscrição para administradores usando o ponto de extremidade do Azure AD v2 `/adminconsent` .  Confira as [instruções sobre como criar uma URL de consentimento de administrador](https://developer.microsoft.com/graph/docs/concepts/auth_v2_service#3-get-administrator-consent) para obter mais informações.

> [!NOTE]
> A criação da URL de consentimento do administrador do locatário requer um URI de redirecionamento/URL de resposta configurado no [portal de registro do aplicativo](https://apps.dev.microsoft.com/). Para adicionar URLs de resposta para o bot, acesse o registro de bot, escolha opções avançadas-> editar manifesto de aplicativo.  Adicione a URL de redirecionamento à `replyUrls` coleção.

> [!IMPORTANT]
> Sempre que você fizer uma alteração nas permissões do aplicativo, também deverá repetir o processo de consentimento do administrador. As alterações feitas no portal de registro de aplicativos não serão refletidas até que o consentimento tiver sido reaplicado pelo administrador do locatário.
