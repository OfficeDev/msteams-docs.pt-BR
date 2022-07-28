---
title: Canais compartilhados
author: Rajeshwari-v
description: Colaborando com canais compartilhados.
ms.author: surbhigupta
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 96cd3014fa1cee38832724e1b50cf29db372d711
ms.sourcegitcommit: d40ea0d504db66d49bbe0955f7031db1cd210056
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2022
ms.locfileid: "67060038"
---
# <a name="shared-channels"></a>Canais compartilhados

Os canais compartilhados no Microsoft Teams permitem que os membros de um canal colaborem com usuários em outras equipes e organizações. Você pode criar e compartilhar um canal compartilhado com:

* Membros de outra equipe dentro da mesma organização.
* Indivíduos dentro da mesma organização.
* Indivíduos e outras equipes de outras organizações.

Os canais compartilhados facilitam a colaboração perfeitamente. Permitir que usuários externos fora da sua organização colaborem com usuários internos no Teams sem alterar o contexto do usuário. Aprimorar a experiência do usuário, ao contrário do uso de contas de convidado, por exemplo, os membros devem sair do Teams e entrar novamente usando uma conta de convidado. Os aplicativos do Teams agora podem estender o poderoso espaço de colaboração.

:::image type="content" source="~/assets/images/app-fundamentals/shared-channels-teams.png" alt-text="Imagem de Canal Compartilhado"border="true" :::

## <a name="manifest-update-in-shared-channels"></a>Atualização de manifesto em canais compartilhados

Quando a experiência do usuário de conteúdo é carregada em um canal compartilhado, use os dados recebidos `getContext` da chamada para alterações de canal compartilhado. `getContext` a chamada publica duas novas propriedades e `hostTeamGroupID` `hostTenantID`, que são usadas para recuperar a associação de canal usando APIs do Microsoft Graph. `hostTeam` é a equipe que cria o canal compartilhado.

SupportedChannelTypes é uma propriedade opcional que habilita seu aplicativo em canais não padrão. Se seu aplicativo der suporte ao escopo da equipe e a propriedade for definida, o Teams habilitará seu aplicativo em cada tipo de canal adequadamente. No momento, há suporte para canais privados e compartilhados. Para obter mais informações, [consulte supportedChannelTypes](../../resources/schema/manifest-schema.md#supportedchanneltypes)

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
> * Se o aplicativo der suporte ao escopo da equipe, ele funcionará em canais padrão, independentemente de quais valores são definidos nessa propriedade.
> * Seu aplicativo pode precisar levar em conta as propriedades exclusivas de cada um desses tipos de canal para funcionar corretamente.

Para obter mais informações sobre como habilitar sua guia, consulte:

* [Obter contexto para sua guia para canais privados](../../tabs/how-to/access-teams-context.md#retrieve-context-in-private-channels)
* [Obter contexto para sua guia para canais compartilhados](../../tabs/how-to/access-teams-context.md#retrieve-context-in-microsoft-teams-connect-shared-channels)

## <a name="apps-and-permissions-in-shared-channels"></a>Aplicativos e permissões em canais compartilhados

Você pode colaborar com membros externos fora da sua organização usando canais compartilhados. As permissões de aplicativo em canais compartilhados seguem a lista de aplicativos da equipe host e a política de aplicativo do locatário do host.

> [!NOTE]
> A [API de notificação do feed de](/graph/teams-send-activityfeednotifications) atividades não dá suporte a notificações entre locatários para aplicativos em um canal compartilhado.

## <a name="get-shared-channel-membership"></a>Obter associação de canal compartilhado

Você pode obter a associação direta de canal compartilhado usando as `hostTeamGroupID` seguintes `getContext` etapas:

1. Obtenha membros diretos com a [API de API de membros do canal GET](/graph/api/channel-list-members?view=graph-rest-beta&tabs=http&preserve-view=true) .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/members
    ```

2. Obtenha cada equipe compartilhada com a API GET `sharedWithTeams` .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/sharedWithTeams
    ```

3. Use membros GET de cada equipe compartilhada (Equipe X) com a API GET `sharedWithTeams` .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/sharedWithTeams/{teamX}/members
    ```

## <a name="classify-members-in-the-shared-channel-as-in-tenant-or-out-tenant"></a>Classificar membros no canal compartilhado como no locatário ou fora do locatário

Você pode classificar membros como no locatário ou fora do `tenantID` locatário comparando o membro ou a equipe com `hostTeamTenantID` o seguinte:

1. Obtenha o membro que você deseja comparar.

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/members
    ```

2. Use `getContext`, compare `tenantID` o membro com a `hostTenantID` propriedade.

## <a name="azure-ad-native-identity"></a>Azure AD identidade nativa

Os aplicativos devem funcionar entre locatários na instalação e no uso. A tabela a seguir lista os tipos de canal e suas IDs de grupo correspondentes:

|Tipo de canal| groupId | hostTeamGroupId |
|----------|---------|-----------------|
|Regular | ID Azure AD grupo de equipe | ID Azure AD grupo de equipe |
|Compartilhados | Vazio | ID do grupo Azure AD equipe host |

## <a name="see-also"></a>Confira também

* [Compilar guias para o Teams](../../tabs/what-are-tabs.md)
* [Esquema de manifesto do aplicativo do Teams](../../resources/schema/manifest-schema.md)
