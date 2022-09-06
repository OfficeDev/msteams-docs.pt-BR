---
title: Estender o aplicativo de guia com permissões do Microsoft Graph
description: Configure permissões e escopos adicionais com o Microsoft Graph para habilitar o SSO (logon único).
ms.topic: how-to
ms.localizationpriority: high
keywords: guias de autenticação de equipes do Microsoft Azure Active Directory (AD do Azure) do escopo do token de acesso de permissão delegada da API do Graph
ms.openlocfilehash: 3232d1104a715b8c50f39b1e70d58fa18d970b7c
ms.sourcegitcommit: d92e14fad6567fe91fd52ee6c213836740316683
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2022
ms.locfileid: "67605086"
---
# <a name="extend-tab-app-with-microsoft-graph-permissions-and-scope"></a>Estender o aplicativo de guia com permissões e escopo do Microsoft Graph

Você pode estender seu aplicativo de guia usando o Microsoft Graph para permitir aos usuários permissões adicionais, como exibir o perfil de usuário do aplicativo, ler emails e muito mais. Seu aplicativo precisa solicitar escopos de permissão específicos para obter os tokens de acesso com o consentimento do usuário do aplicativo.

Escopos do Graph, como `User.Read` ou `Mail.Read`, permitem especificar como seu aplicativo acessa a conta de um usuário do Teams. É preciso especificar seus escopos na solicitação da autorização.

Nesta seção, você aprenderá a:

- [Configurar as permissões da API no Azure AD](#configure-api-permissions-in-azure-ad)
- [Configurar a autenticação para diferentes plataformas](#configure-authentication-for-different-platforms)
- [Adquirir o token de acesso para o MS Graph](#acquire-access-token-for-ms-graph)

## <a name="configure-api-permissions-in-azure-ad"></a>Configurar as permissões da API no Azure AD

Você pode configurar escopos adicionais do Graph no Azure AD para seu aplicativo. Essas são permissões delegadas, usadas por aplicativos que exigem acesso conectado. Um usuário ou o administrador do aplicativo conectado deve consentir com eles. Seu aplicativo de guia pode consentir em nome do usuário conectado ao chamar o Microsoft Graph.

### <a name="to-configure-api-permissions"></a>Para configurar as permissões da API

1. Abra o aplicativo que você registrou no [portal do Azure](https://ms.portal.azure.com/).

2. Selecione **Gerenciar** > **permissões da API** do painel esquerdo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/api-permission-menu.png" alt-text="Opção do menu de permissões do aplicativo":::

    A página **Permissões da AP** é exibida.

3. Selecione **Adicionar permissões** para adicionar as permissões da API do Microsoft Graph.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-permission.png" alt-text="Página de permissões do aplicativo.":::

    A página **Solicitar permissões da API** é exibida.

4. Selecione **Microsoft Graph**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/request-api-permission.png" alt-text="Página de solicitação de permissões da API.":::

    As opções de permissões de Graph são exibidas.

5. Selecione **Permissões delegadas** para exibir a lista de permissões.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/delegated-permission.png" alt-text="Permissões delegadas.":::

6. Selecione as permissões relevantes para seu aplicativo e, em seguida, selecione **Adicionar permissões**.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-permission.png" alt-text="Selecionar permissões.":::

    Você também pode inserir o nome da permissão na caixa de pesquisa para encontrá-lo.

    Uma mensagem aparece no navegador informando que as permissões foram atualizadas.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/updated-permission-msg.png" alt-text="Mensagem atualizada de permissões.":::

    As permissões adicionadas são exibidas na página **Permissões da API**.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/configured-permissions.png" alt-text="As permissões da API estão configuradas.":::

    Você configurou seu aplicativo com as permissões do Microsoft Graph.

## <a name="configure-authentication-for-different-platforms"></a>Configurar a autenticação para diferentes plataformas

Dependendo da plataforma ou dispositivo para o qual você deseja direcionar seu aplicativo, configurações adicionais podem ser necessárias, como URIs de redirecionamento, configurações de autenticação específicas ou detalhes específicos da plataforma.

> [!NOTE]
>
> - Se seu aplicativo de guia não recebeu o consentimento do administrador de TI, os usuários do aplicativo precisarão dar consentimento na primeira vez que usarem seu aplicativo em uma plataforma diferente.
> - A concessão implícita não é necessária se a SSO estiver habilitada em um aplicativo de guia.

Você pode configurar a autenticação para várias plataformas, desde que o URL seja exclusivo.

### <a name="to-configure-authentication-for-a-platform"></a>Para configurar a autenticação para uma plataforma

1. Abra o aplicativo que você registrou no [portal do Azure](https://ms.portal.azure.com/).

1. Selecione **Gerenciar** > **Autenticação** no painel esquerdo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal-platform.png" alt-text="Autenticar para plataformas":::

    A página **Configurações da plataforma** é exibida.

1. Selecione **Adicionar uma plataforma**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-platform.png" alt-text="Adicionar uma plataforma":::

    A página **Configurar plataformas** é exibida.

1. Selecione a plataforma que você deseja configurar para seu aplicativo de guia. Você pode escolher o tipo de plataforma Web ou SPA.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/configure-platform.png" alt-text="Selecione a plataforma Web ":::

    Você pode configurar várias plataformas para um tipo específico de plataforma. Verifique se o URI de redirecionamento é exclusivo para cada plataforma configurada.

    A página Configurar Web é exibida.

    > [!NOTE]
    > As configurações serão diferentes com base na plataforma que você selecionou.

1. Insira os detalhes da configuração para a plataforma.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/config-web-platform.png" alt-text="Configurar a plataforma Web ":::

    1. Insira o URI de redirecionamento. A URI deve ser exclusiva.
    2. Insira a URL de logoff do canal frontal.
    3. Selecione os tokens que você deseja que o Azure AD envie para seu aplicativo.

1. Selecione **Configurar**.

    A plataforma é configurada e exibida na página **Configurações da plataforma**.

## <a name="acquire-access-token-for-ms-graph"></a>Adquira o token de acesso para o MS Graph

Você precisará adquirir o token de acesso para o Microsoft Graph. Você pode fazer isso usando o fluxo de OBO do Azure AD.

A implementação atual da SSO dá consentimento apenas para permissões no nível do usuário que não são utilizáveis para fazer chamadas do Graph. Para obter as permissões (escopos) necessárias para fazer uma chamada de Graph, os aplicativos de SSO devem implementar um serviço Web personalizado para trocar o token recebido do SDK JavaScript do Teams por um token que inclua os escopos necessários. Você pode usar a Biblioteca de Autenticação da Microsoft (MSAL) para buscar o token do lado do cliente.

Depois de configurar as permissões do Graph no Azure AD:

- [Configure seu código do lado do cliente para buscar o token de acesso usando a MSAL](#configure-code-to-fetch-access-token-using-msal)
- [Passe o token de acesso para o código ao lado do servidor](#pass-the-access-token-to-server-side-code)

### <a name="configure-code-to-fetch-access-token-using-msal"></a>Configure o código para buscar o token de acesso usando a MSAL

O código a seguir fornece um exemplo de fluxo de OBO para buscar o token de acesso do cliente do Teams usando a MSAL.

### <a name="c"></a>[C#](#tab/dotnet)

```csharp

IConfidentialClientApplication app = ConfidentialClientApplicationBuilder.Create(<"Client id">)
                                                .WithClientSecret(<"Client secret">)
                                                .WithAuthority($"https://login.microsoftonline.com/<"Tenant id">")
                                                .Build();
 
            try
            {
                var idToken = <"Client side token">;
                UserAssertion assert = new UserAssertion(idToken);
                List<string> scopes = new List<string>();
                scopes.Add("https://graph.microsoft.com/User.Read");
                var responseToken = await app.AcquireTokenOnBehalfOf(scopes, assert).ExecuteAsync();
                return responseToken.AccessToken.ToString();
            }
            catch (Exception ex)
            {
                return ex.Message;
            }
        }
```

### <a name="nodejs"></a>[Node.js](#tab/nodejs)

```Node.js

// Exchange client Id side token with server token
  app.post('/getProfileOnBehalfOf', function(req, res) {
        var tid = < "Tenant id" >
    var token = < "Client side token" >
    var scopes = ["https://graph.microsoft.com/User.Read"];

        // Creating MSAL client
        const msalClient = new msal.ConfidentialClientApplication({
            auth: {
                clientId: < "Client ID" >,
                clientSecret: < "Client Secret" >
      }
        });

        var oboPromise = new Promise((resolve, reject) => {
            msalClient.acquireTokenOnBehalfOf({
                authority: `https://login.microsoftonline.com/${tid}`,
                oboAssertion: token,
                scopes: scopes,
                skipCache: true
            }).then(result => {
                console.log("Token is: " + result.accessToken);
            }).catch(error => {
                reject({ "error": error.errorCode });
            });
        });
```

---

### <a name="pass-the-access-token-to-server-side-code"></a>Passe o token de acesso para o código ao lado do servidor

Se você precisar acessar dados do Microsoft Graph, configure o código do lado do servidor para:

1. Valide o token de acesso. Para saber mais, confira [Validar o token de acesso](tab-sso-code.md#validate-the-access-token).
1. Inicie o fluxo de OBO do OAuth 2.0 com uma chamada para a plataforma de identidade da Microsoft que inclui o token de acesso, alguns metadados sobre o usuário e as credenciais do aplicativo de guia (sua ID de aplicativo e segredo do cliente). A plataforma de identidade da Microsoft retornará um novo token de acesso que pode ser usado para acessar o Microsoft Graph.
1. Obter os dados do Microsoft Graph usando o novo token.
1. Se necessário, use a serialização de cache de token no MSAL.NET para armazenar em cache o novo token de acesso para vários.

> [!IMPORTANT]
> Como prática recomendada de segurança, use sempre o código do lado do servidor para fazer as chamadas do Microsoft Graph ou outras chamadas que exijam a passagem de um token de acesso. Nunca retorne o token OBO ao cliente para permitir que o cliente faça chamadas diretas ao Microsoft Graph. Isso ajuda a proteger o token de ser interceptado ou vazado.

## <a name="known-limitations"></a>Limitações conhecidas

Consentimento do administrador do locatário: uma maneira simples de [consentir em nome de uma organização como administrador de locatários](/azure/active-directory/manage-apps/consent-and-permissions-overview#admin-consent) é obter o [consentimento do administrador](/azure/active-directory/manage-apps/grant-admin-consent).

Você pode solicitar o consentimento usando a API de Autenticação. Outra abordagem para obter os escopos de Graph é apresentar uma caixa de diálogo de consentimento usando nossa [abordagem de autenticação do provedor OAuth de terceiros](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page). Essa abordagem envolve o surgimento de uma caixa de diálogo de consentimento do Azure AD.

<details>
<summary>Para solicitar consentimento adicional usando a API Auth, siga estas etapas:</summary>

1. O token recuperado usando `getAuthToken()` deve ser trocado no lado do servidor usando o Azure AD [em nome do fluxo](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) para obter acesso a essas outras APIs do Graph. Certifique-se de usar o ponto de extremidade v2 Graph para esta troca.
2. Se a troca falhar, o Microsoft Azure AD retornará uma exceção de concessão inválida. Ele geralmente responde com uma das duas mensagens de erro, `invalid_grant` ou `interaction_required`.
3. Quando a troca falhar, você deve solicitar consentimento. Utilize a interface do usuário (UI) para solicitar que o usuário do aplicativo dê outro consentimento. Esta interface do usuário precisa incluir um botão que aciona uma caixa de diálogo de consentimento do Azure AD usando a [Autenticação silenciosa](~/concepts/authentication/auth-silent-aad.md).
4. Ao solicitar mais consentimento do Azure AD, você precisa incluir `prompt=consent` no seu [parâmetro de sequência de consulta](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) para o Azure AD, caso contrário, o Azure AD não solicitaria outros escopos.
    - Em vez de `?scope={scopes}`, use `?prompt=consent&scope={scopes}`
    - Certifique-se de que `{scopes}` inclua todos os escopos que você está solicitando ao usuário, por exemplo, `Mail.Read` ou `User.Read`.
5. Depois que o usuário do aplicativo conceder mais permissões, tente novamente o fluxo de OBO para obter acesso a essas outras APIs.

    </details>

## <a name="see-also"></a>Confira também

- [Fluxo em Nome do OAuth 2.0 ](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow)
- [Obter acesso para o MS Graph](/graph/auth-v2-user)
- [Serialização de cache de token no MSAL.NET](/azure/active-directory/develop/msal-net-token-cache-serialization?tabs=aspnet)
- [Provedor MSAL2 do Microsoft Teams](/graph/toolkit/providers/teams-msal2)
