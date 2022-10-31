---
title: Conexão Teams canais compartilhados
author: Rajeshwari-v
description: Saiba mais sobre Conexão Teams canais compartilhados para colaborar com usuários internos e externos com segurança em um espaço compartilhado sem alternar locatários.
ms.author: surbhigupta
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: d1f2d212c33f80ce6a5d27e93bda0551d26542dd
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789923"
---
# <a name="microsoft-teams-connect-shared-channels"></a>Conexão Microsoft Teams canais compartilhados

Conexão Microsoft Teams canais compartilhados permitem que membros de um canal colaborem com usuários em outras equipes e organizações. Você pode criar e compartilhar um canal compartilhado com:

* Membros de outra equipe dentro da mesma organização.
* Indivíduos dentro da mesma organização.
* Indivíduos e outras equipes de outras organizações.

Conexão Teams canais compartilhados facilitam a colaboração segura perfeitamente. Permitir que usuários externos fora de sua organização colaborem com usuários internos no Teams sem alterar o contexto do usuário. Aprimorar a experiência do usuário ao contrário do uso de contas de convidado, por exemplo, os membros devem sair do Teams e entrar novamente usando uma conta de convidado. Os aplicativos do Teams estendem o espaço de colaboração poderoso.

:::image type="content" source="~/assets/images/app-fundamentals/shared-channels-teams.png" alt-text="Diagrama que mostra a Equipe B da organização A e a Equipe C da organização B colaborando em um Canal compartilhado como Equipe A." border="true" :::

## <a name="enable-your-app-for-shared-channels"></a>Habilitar seu aplicativo para canais compartilhados

SupportedChannelTypes é uma propriedade opcional que habilita seu aplicativo em canais não padrão. Se o aplicativo der suporte ao escopo da equipe e a propriedade estiver definida, o Teams habilitará seu aplicativo em cada tipo de canal de acordo. No momento, há suporte para canais privados e compartilhados. Para obter mais informações, consulte [SupportedChannelTypes](../../resources/schema/manifest-schema.md#supportedchanneltypes).

```JSON
"supportedChannelTypes": {
      "type": "array",
      "description": "List of ‘non-standard’ channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope. ",
      "maxItems": 2,
      "items": { 
        "enum": [
          "sharedChannels",
          "privateChannels"
        ]
      }
    }
```

> [!NOTE]
>
> * Se o aplicativo der suporte ao escopo da equipe, ele funcionará em canais padrão, independentemente dos valores definidos nesta propriedade.
> * Seu aplicativo pode precisar contabilizar as propriedades exclusivas de cada um desses tipos de canal para funcionar corretamente.

## <a name="get-context-for-shared-channels"></a>Obter contexto para canais compartilhados

Quando a UX de conteúdo for carregada em um canal compartilhado, use os dados recebidos da chamada para alterações de `getContext` canal compartilhado. `getContext` call publica duas novas propriedades `hostTeamGroupID` e `hostTenantID`, que são usadas para recuperar a associação de canal usando APIs do Microsoft Graph. `hostTeam` é a equipe que cria o canal compartilhado.

Para obter mais informações para habilitar sua guia, confira:

* [Obter contexto para sua guia para canais privados](../../tabs/how-to/access-teams-context.md#retrieve-context-in-private-channels)
* [Obter contexto em canais compartilhados](../../tabs/how-to/access-teams-context.md#get-context-in-shared-channels)

## <a name="apps-and-permissions-in-shared-channels"></a>Aplicativos e permissões em canais compartilhados

Você pode colaborar com membros externos fora de sua organização usando canais compartilhados. As permissões de aplicativo em canais compartilhados seguem a lista de aplicativos da equipe de host e a política de aplicativo do locatário do host.

> [!NOTE]
> A [API de notificação do feed de atividades](/graph/teams-send-activityfeednotifications) não dá suporte a notificações entre locatários para aplicativos em um canal compartilhado.

## <a name="get-shared-channel-membership"></a>Obter associação de canal compartilhado

Você pode obter associação direta de canal compartilhado usando as `hostTeamGroupID` `getContext` seguintes etapas:

1. Obtenha membros diretos com [a API de API de membros do canal GET](/graph/api/channel-list-members?view=graph-rest-beta&tabs=http&preserve-view=true) .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/members
    ```

2. Obtenha cada equipe compartilhada com a API GET `sharedWithTeams` .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/sharedWithTeams
    ```

3. Use membros GET de cada equipe compartilhada (Team X) com a API GET `sharedWithTeams` .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/sharedWithTeams/{teamX}/members
    ```

## <a name="classify-members-in-the-shared-channel-as-in-tenant-or-out-tenant"></a>Classificar membros no canal compartilhado como locatário ou locatário

Você pode classificar os membros como in-tenant ou out-tenant comparando `tenantID` o membro ou a equipe com `hostTeamTenantID` o seguinte:

1. Obtenha o membro que você deseja comparar.

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/members
    ```

2. Use `getContext`, compare o `tenantID` do membro com a `hostTenantID` propriedade.

## <a name="azure-ad-native-identity"></a>Azure AD identidade nativa

Os aplicativos devem funcionar entre locatários na instalação e no uso. A tabela a seguir lista os tipos de canal e suas IDs de grupo correspondentes:

|Tipo de canal| groupId | hostTeamGroupId |
|----------|---------|-----------------|
|Regular | ID do grupo Azure AD equipe | ID do grupo Azure AD equipe |
|Compartilhados | Vazio | ID do grupo do Host Team Azure AD |

## <a name="see-also"></a>Confira também

* [Compilar guias para o Teams](../../tabs/what-are-tabs.md)
* [Esquema de manifesto do aplicativo para o Teams](../../resources/schema/manifest-schema.md)
* [Canais compartilhados no Microsoft Teams](/MicrosoftTeams/shared-channels)
* [Tipo de recurso de canal](/graph/api/resources/channel)
* [Política de retenção para locais do Teams](/microsoft-365/compliance/create-retention-policies)
