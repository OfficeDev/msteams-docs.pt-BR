---
title: Atualizar manifesto para habilitar o SSO para guias
description: Descreve o manifesto de atualização para habilitar o SSO para guias
ms.topic: how-to
ms.localizationpriority: medium
keywords: guias de autenticação do teams Microsoft Azure Active Directory (Azure AD) API do Graph
ms.openlocfilehash: 90a1ac781ef521f4b236bdf26f50d44533fa815a
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558734"
---
# <a name="update-manifest-for-sso-and-preview-app"></a>Atualizar manifesto para SSO e aplicativo de visualização

Antes de atualizar o manifesto do aplicativo Teams, verifique se você configurou o código para habilitar o SSO em seu aplicativo guia.

> [!div class="nextstepaction"]
> [Configurar código](tab-sso-code.md)

Você registrou seu aplicativo guia no Azure AD e obteve uma ID do aplicativo. Você também configurou seu código para chamar e `getAuthToken()` manipular o token de acesso. Agora, você deve atualizar o manifesto do aplicativo Teams para habilitar o SSO para seu aplicativo de guia. O manifesto do aplicativo Teams descreve como um aplicativo se integra ao Teams.

## <a name="webapplicationinfo-property"></a>Propriedade webApplicationInfo

Configure a propriedade `webApplicationInfo` no arquivo de manifesto do aplicativo Teams. Essa propriedade permite que o SSO para seu aplicativo ajude os usuários do aplicativo a acessar seu aplicativo guia perfeitamente.

&nbsp;&nbsp;:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sso-manifest.png" alt-text="Configuração do manifesto do aplicativo Teams":::

`webApplicationInfo` tem dois elementos e `id` `resource`.

| Elemento | Descrição |
| --- | --- |
| id | Insira a ID do aplicativo (GUID) que você criou Azure AD. |
| recurso | Insira o URI do subdomínio do aplicativo e o URI da ID do aplicativo que você criou Azure AD ao criar o escopo. Você pode copiá-lo do **Azure AD** >  **Expose de uma seção de API**. |

> [!NOTE]
> Use o manifesto versão 1.5 ou superior para implementar a `webApplicationInfo` propriedade.

O URI da ID do aplicativo registrado no Azure AD está configurado com o escopo da API que você expôs. Configure o URI `resource` `getAuthToken()` do subdomínio do aplicativo para garantir que a solicitação de autenticação usada seja do domínio fornecido no manifesto do aplicativo Teams.

Para obter mais informações, consulte [webApplicationInfo](../../../resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="to-configure-teams-app-manifest"></a>Para configurar o manifesto do aplicativo Teams

1. Abra o projeto de aplicativo de guia.
2. Abra a pasta de manifesto.

  > [!NOTE]
  >
  > - A pasta de manifesto deve estar na raiz do seu projeto. Para obter mais informações, [consulte Criar um pacote de aplicativos do Microsoft Teams](../../../concepts/build-and-test/apps-package.md).
  > - Para obter mais informações sobre como aprender a criar um manifest.json, consulte [Referência: esquema de manifesto para o Microsoft Teams](../../../resources/schema/manifest-schema.md).

1. Abrir o arquivo manifest.json
1. Acrescente o seguinte snippet de código ao arquivo de manifesto para adicionar a nova propriedade:

    ```json
    "webApplicationInfo": {
    "id": "{Azure AD AppId}",
    "resource": "api://{Subdomain}.example.com/{Azure AD AppId}"
    }
    ```

    Onde
    - {Azure AD AppId} é a ID do aplicativo que você criou quando registrou seu aplicativo no Azure AD. É o GUID.
    - {{Subdomain}.app ID URI} é o URI da ID do aplicativo que você registrou ao criar o escopo Azure AD.

4. Atualize a ID do aplicativo Azure AD na propriedade **de ID**.
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
  "packageName": "com.contoso.teamsauthsso",
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
> Durante a depuração, você pode usar o ngrok para testar seu aplicativo Azure AD. Nesse caso, você precisa substituir o subdomínio pela `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` URL ngrok. Você precisará atualizar a URL sempre que o subdomínio ngrok for alterado, por exemplo, api://23c3-103-50-148-128.ngrok.io/bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c.

## <a name="sideload-and-preview-in-teams"></a>Sideload e visualização no Teams

Você configurou o aplicativo guia para habilitar o SSO no Azure AD, no código do aplicativo e no arquivo de manifesto do Teams. Agora você pode fazer o sideload do aplicativo de guias no Teams e visualiza-lo no ambiente do Teams.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sso-flow.png" alt-text="Aplicativo de SSO":::

Para visualizar seu aplicativo de guia no Teams:

1. Crie um pacote do aplicativo.

   O pacote do aplicativo é um arquivo zip que contém o arquivo de manifesto do aplicativo e os ícones do aplicativo.

1. Abra o Teams.

1. Selecione **Aplicativos** > **Gerenciar seus aplicativos** > **Carregar um aplicativo**.

    As opções para carregar um aplicativo são exibidas.

1. Selecione **Carregar um aplicativo personalizado para** fazer o sideload do aplicativo guia no Teams.

1. Selecione o arquivo zip do pacote do aplicativo e, em seguida, **selecione Adicionar**.

    O aplicativo de guia é sideload e a caixa de diálogo aparece para informá-lo sobre as permissões adicionais que podem ser necessárias.

1. Selecione **Continuar**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/teams-sso-consent.png" alt-text="Caixa de diálogo do Teams informando sobre permissões adicionais necessárias":::

    A caixa Azure AD de consentimento do usuário é exibida.

1. Selecione **Aceitar** para dar consentimento para escopos de ID aberta.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/aad-sso-consent.png" alt-text="Azure AD de consentimento":::

    O Teams abre o aplicativo guia e você pode usá-lo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/teams-sso-app.png" alt-text="Exemplo de aplicativo de guia do Teams com SSO habilitado":::

    Parabéns! Você habilitou o SSO para seu aplicativo de guia.

## <a name="see-also"></a>Confira também

- [Esquema de manifesto para o Microsoft Teams](../../../resources/schema/manifest-schema.md)
- [Formato do esquema de manifesto](https://developer.microsoft.com/json-schemas/teams/v1.12/MicrosoftTeams.schema.json)
- [Criar um pacote de aplicativo do Microsoft Teams](../../../concepts/build-and-test/apps-package.md)
