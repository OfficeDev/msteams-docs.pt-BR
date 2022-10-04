---
title: Atualizar manifesto para habilitar o SSO para guias
description: Atualize o manifesto do Teams para habilitar o SSO (logon único) para guias e fazer sideload dele no cliente do Teams para testar a autenticação de SSO.
ms.topic: how-to
ms.localizationpriority: high
keywords: guias de autenticação do teams Microsoft Azure Active Directory (Azure AD) API do Graph
ms.openlocfilehash: bd5b7257a131a11e861b94221c533d8364b6bb54
ms.sourcegitcommit: 176bbca74ba46b7ac298899d19a2d75087fb37c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68376582"
---
# <a name="update-manifest-for-sso-and-preview-app"></a>Atualizar manifesto para SSO e aplicativo de visualização

Antes de atualizar o manifesto do aplicativo Teams, verifique se você configurou o código para habilitar o SSO em seu aplicativo guia.

> [!div class="nextstepaction"]
> [Configurar código](tab-sso-code.md)

Você registrou seu aplicativo guia no Azure AD e obteve uma ID do aplicativo. Você também configurou seu código para chamar `getAuthToken()` e manipular o token de acesso. Agora, você deve atualizar o manifesto do aplicativo Teams para habilitar o SSO para seu aplicativo guia. O manifesto do aplicativo Teams descreve como um aplicativo se integra ao Teams.

## <a name="webapplicationinfo-property"></a>propriedade webApplicationInfo

Configure a propriedade `webApplicationInfo` no arquivo de manifesto do aplicativo Teams. Essa propriedade habilita o SSO para seu aplicativo para ajudar os usuários do aplicativo a acessar seu aplicativo guia diretamente.

&nbsp;&nbsp;:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sso-manifest.png" alt-text="Configuração do manifesto do aplicativo":::

`webApplicationInfo` tem dois elementos, `id` e `resource`.

| Elemento | Descrição |
| --- | --- |
| id | Insira a ID do aplicativo (GUID) que você criou no Azure AD. |
| recurso | Insira o URI do subdomínio do aplicativo e o URI da ID do aplicativo que você criou no Azure AD ao criar o escopo. Você pode copiá-lo do **Azure AD** > **Expor uma seção de API**. |

> [!NOTE]
> Use o manifesto versão 1.5 ou superior para implementar a propriedade `webApplicationInfo`.

O URI da ID do aplicativo que você registrou no Azure AD está configurado com o escopo da API que você expôs. Configure o URI do subdomínio do aplicativo no `resource` para garantir que a solicitação de autenticação usando `getAuthToken()` seja do domínio fornecido no manifesto do aplicativo Teams.

Para obter mais informações, consulte [webApplicationInfo](../../../resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="to-configure-teams-app-manifest"></a>Para configurar o manifesto do aplicativo Teams

1. Abra o projeto de aplicativo guia.
2. Abra a pasta de manifesto.

  > [!NOTE]
  >
  > - A pasta de manifesto deve estar na raiz do seu projeto. Para obter mais informações, consulte [Criar um pacote de aplicativos do Microsoft Teams](../../../concepts/build-and-test/apps-package.md).
  > - Para obter mais informações sobre como aprender a criar um manifest.json, consulte [Referência: Esquema de manifesto para o Microsoft Teams](../../../resources/schema/manifest-schema.md).

1. Abrir o arquivo manifest.json
1. Acrescente o seguinte trecho de código ao arquivo de manifesto para adicionar a nova propriedade:

    ```json
    "webApplicationInfo": {
    "id": "{Azure AD AppId}",
    "resource": "api://{Subdomain}.example.com/{Azure AD AppId}"
    }
    ```

    Onde
    - {Azure AD AppId} é a ID do aplicativo que você criou quando registrou seu aplicativo no Azure AD. É o GUID.
    - {{Subdomain}.app ID URI} é o URI da ID do aplicativo que você registrou ao criar o escopo no Azure AD.

4. Atualize a ID do aplicativo do Azure AD na propriedade **id**.
5. Atualize a URL do subdomínio nas seguintes propriedades:
   1. `contentUrl`
   2. `configurationUrl`
   3. `validDomains`
6. Salve o arquivo de manifesto do aplicativo Teams.

<br>
<details>
<summary>Aqui está um exemplo de manifesto do aplicativo depois que ele é atualizado</summary>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
  "manifestVersion": "1.11",
  "version": "1.0.0",
  "id": "bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c",
  "developer": {
    "name": "Microsoft",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com/privacy",
    "termsOfUseUrl": "https://www.microsoft.com/termsofuse"
  },
  "name": {
    "short": "Teams Auth SSO",
    "full": "Teams Auth SSO"
  },
  "description": {
    "short": "Teams Auth SSO app",
    "full": "The Teams Auth SSO app"
  },
  "icons": {
    "outline": "outline.png",
    "color": "color.png"
  },
  "accentColor": "#60A18E",
  "staticTabs": [
    {
      "entityId": "auth",
      "name": "Auth",
      "contentUrl": "https://contoso.com/Home/Index",
      "scopes": [ "personal" ]
    }
  ],
  "configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/Home/Configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "team"
      ]
    }
  ],
  "permissions": [ "identity", "messageTeamMembers" ],
  "validDomains": [
    "contoso.com"
  ],
  "webApplicationInfo": {
    "id": "bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c",
    "resource": "api://contoso.com/bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c"
  }
}
```

</details>

> [!NOTE]
> Durante a depuração, você pode usar o ngrok para testar seu aplicativo no Azure AD. Nesse caso, você precisa substituir o subdomínio em `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` pela URL ngrok. Você precisará atualizar a URL sempre que o subdomínio ngrok for alterado, por exemplo, api://23c3-103-50-148-128.ngrok.io/bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c.

## <a name="sideload-and-preview-in-teams"></a>Sideload e Visualização no Teams

Você configurou o aplicativo guia para habilitar o SSO no Azure AD, no código do aplicativo e no arquivo de manifesto do Teams. Agora você pode fazer o sideload do aplicativo guia no Teams e visualiza-lo no ambiente do Teams.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sso-flow.png" alt-text="Aplicativo SSO":::

Para visualizar seu aplicativo guia no Teams:

1. Crie um pacote de aplicativos.

   O pacote do aplicativo é um arquivo zip que contém o arquivo de manifesto do aplicativo e os ícones do aplicativo.

1. Abra o Teams.

1. Selecione **Aplicativos** > **Gerencie seus aplicativos** > **Carregue um aplicativo**.

    As opções para carregar um aplicativo são exibidas.

1. Selecione **Carregue um aplicativo personalizado** para realizar o sideload do aplicativo guia no Teams.

1. Selecione o arquivo zip do pacote do aplicativo e selecione **Adicionar**.

    O aplicativo guia é sideload e a caixa de diálogo é exibida para informá-lo sobre as permissões adicionais que podem ser necessárias.

1. Selecione **Continuar**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/teams-sso-consent.png" alt-text="Caixa de diálogo do Teams informando sobre permissões adicionais necessárias":::

    A caixa de diálogo de consentimento do Azure AD é exibida.

1. Selecione **Aceitar** para dar consentimento para escopos de open-id.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/aad-sso-consent.png" alt-text="Caixa de diálogo de consentimento do Azure AD":::

    O Teams abre o aplicativo guia e você pode usá-lo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/teams-sso-app.png" alt-text="Exemplo do aplicativo guia do Teams com o SSO habilitado":::

    Parabéns! Você habilitou o SSO para seu aplicativo guia.

## <a name="see-also"></a>Confira também

- [Esquema de manifesto para o Microsoft Teams](../../../resources/schema/manifest-schema.md)
- [Formato do esquema de manifesto](https://developer.microsoft.com/json-schemas/teams/v1.12/MicrosoftTeams.schema.json)
- [Criar um pacote de aplicativo do Microsoft Teams](../../../concepts/build-and-test/apps-package.md)
