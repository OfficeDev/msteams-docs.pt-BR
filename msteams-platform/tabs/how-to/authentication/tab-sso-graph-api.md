---
title: Estender o aplicativo guia com permissões do Microsoft Graph
description: Descreve como configurar permissões de API com o Microsoft Graph
ms.topic: how-to
ms.localizationpriority: medium
keywords: guias de autenticação do teams Microsoft Azure Active Directory (Azure AD) API do Graph de token de acesso de permissão delegado
ms.openlocfilehash: 020148e8510e7e9b2ad14b893ccb8531f3a83402
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485290"
---
# <a name="extend-tab-app-with-microsoft-graph-permissions-and-scope"></a>Estender o aplicativo guia com permissões e escopo do Microsoft Graph

Você pode estender seu aplicativo guia usando o Microsoft Graph para permitir aos usuários permissões adicionais, como exibir o perfil do usuário do aplicativo, ler emails e muito mais. Seu aplicativo deve solicitar escopos de permissão específicos para obter os tokens de acesso no consentimento do usuário do aplicativo.

Os escopos de grafo, como `User.Read` ou `Mail.Read`, permitem que você especifique como seu aplicativo acessa a conta de um usuário do Teams. Você precisa especificar seus escopos na solicitação de autorização.

Nesta seção, você aprenderá a:

- [Configurar permissões de API no Azure AD](#configure-api-permissions-in-azure-ad)
- [Configurar a autenticação para diferentes plataformas](#configure-authentication-for-different-platforms)
- [Adquirir token de acesso para o MS Graph](#acquire-access-token-for-ms-graph)

## <a name="configure-api-permissions-in-azure-ad"></a>Configurar permissões de API no Azure AD

Você pode configurar escopos adicionais do Graph Azure AD para seu aplicativo. Essas são permissões delegadas, que são usadas por aplicativos que exigem acesso conectado. Um usuário ou administrador de aplicativo conectado deve consentir com ele. Seu aplicativo guia pode consentir em nome do usuário conectado quando ele chama o Microsoft Graph.

### <a name="to-configure-api-permissions"></a>Para configurar permissões de API

1. Abra o aplicativo que você registrou [no portal do Azure](https://ms.portal.azure.com/).

2. Selecione **Gerenciar** > **permissão de API** no painel esquerdo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/api-permission-menu.png" alt-text="Opção de menu permissões de aplicativo." border="true":::

    A **página de permissões de API** é exibida.

3. Selecione **+ Adicionar permissões para** adicionar permissões API do Graph Microsoft.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-permission.png" alt-text="Página de permissões do aplicativo." border="true":::

    A **página Solicitar permissões de API** é exibida.

4. Selecione **Microsoft Graph**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/request-api-permission.png" alt-text="Página Solicitar permissões de API." border="true":::

    As opções para permissões do Graph são exibidas.

5. Selecione **Permissões delegadas para** exibir a lista de permissões.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/delegated-permission.png" alt-text="Permissões delegadas." border="true":::

6. Selecione permissões relevantes para seu aplicativo e, em seguida, **selecione Adicionar permissões**.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-permission.png" alt-text="Selecione permissões." border="true":::

    Você também pode inserir o nome da permissão na caixa de pesquisa para encontrá-lo.

    Uma mensagem aparece no navegador informando que as permissões foram atualizadas.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/updated-permission-msg.png" alt-text="Mensagem atualizada de permissões." border="false":::

    As permissões adicionadas são exibidas na **página de permissões da** API.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/configured-permissions.png" alt-text="As permissões de API estão configuradas." border="true":::

    Você configurou seu aplicativo com permissões do Microsoft Graph.

## <a name="configure-authentication-for-different-platforms"></a>Configurar a autenticação para diferentes plataformas

Dependendo da plataforma ou do dispositivo para o qual você deseja direcionar seu aplicativo, pode ser necessária configuração adicional, como URIs de redirecionamento, configurações de autenticação específicas ou detalhes específicos da plataforma.

> [!NOTE]
>
> - Se o aplicativo de guia não tiver sido concedido ao administrador de TI, os usuários do aplicativo terão que dar consentimento na primeira vez que usarem seu aplicativo em uma plataforma diferente.
> - A concessão implícita não será necessária se o SSO estiver habilitado em um aplicativo guia.

Você pode configurar a autenticação para várias plataformas, desde que a URL seja exclusiva.

### <a name="to-configure-authentication-for-a-platform"></a>Para configurar a autenticação para uma plataforma

1. Abra o aplicativo que você registrou no [portal do Azure](https://ms.portal.azure.com/).

1. Selecione **Gerenciar** > **Autenticação** no painel esquerdo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal-platform.png" alt-text="Autenticar para plataformas" border="true":::

    A **página Configurações da** plataforma é exibida.

1. Selecione **+ Adicionar uma plataforma**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-platform.png" alt-text="Adicionar uma plataforma" border="true":::

    A **página Configurar plataformas** é exibida.

1. Selecione a plataforma que você deseja configurar para seu aplicativo guia. Você pode escolher o tipo de plataforma da Web ou spa.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/configure-platform.png" alt-text="Selecionar plataforma Web" border="true":::

    Você pode configurar várias plataformas para um tipo de plataforma específico. Verifique se o URI de redirecionamento é exclusivo para cada plataforma que você configurar.

    A página Configurar Web é exibida.

    > [!NOTE]
    > As configurações serão diferentes com base na plataforma selecionada.

1. Insira os detalhes de configuração da plataforma.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/config-web-platform.png" alt-text="Configurar a plataforma Web" border="true":::

    1. Insira o URI de redirecionamento. O URI deve ser exclusivo.
    2. Insira a URL de logoff do canal frontal.
    3. Selecione os tokens que você Azure AD enviar para seu aplicativo.

1. Selecione **Configurar**.

    A plataforma é configurada e exibida na página **configurações da** plataforma.

## <a name="acquire-access-token-for-ms-graph"></a>Adquirir token de acesso para o MS Graph

Você precisará adquirir o token de acesso para o Microsoft Graph. Você pode fazer isso usando o Azure AD OBO.

A implementação atual do SSO concede consentimento apenas para permissões de nível de usuário que não são utilizáveis para fazer chamadas do Graph. Para obter as permissões (escopos) necessárias para fazer uma chamada do Graph, os aplicativos de SSO devem implementar um serviço Web personalizado para trocar o token recebido do SDK javaScript do Teams por um token que inclua os escopos necessários. Você pode usar a MSAL (Biblioteca de Autenticação da Microsoft) para buscar o token do lado do cliente.

Depois de configurar as permissões do Graph Azure AD:

- [Configurar o código do lado do cliente para buscar o token de acesso usando a MSAL](#configure-code-to-fetch-access-token-using-msal)
- [Passe o token de acesso para o código ao lado do servidor](#pass-the-access-token-to-server-side-code)

### <a name="configure-code-to-fetch-access-token-using-msal"></a>Configurar o código para buscar o token de acesso usando a MSAL

O código a seguir fornece um exemplo de fluxo OBO para buscar o token de acesso do cliente do Teams usando a MSAL.

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

Se você precisar acessar os dados do Microsoft Graph, configure o código do lado do servidor para:

1. Valide o token de acesso. Para saber mais, confira [Validar o token de acesso](tab-sso-code.md#validate-the-access-token).
1. Inicie o fluxo OBO do OAuth 2.0 com uma chamada para o plataforma de identidade da Microsoft que inclui o token de acesso, alguns metadados sobre o usuário e as credenciais do aplicativo guia (a ID do aplicativo e o segredo do cliente). A plataforma de identidade da Microsoft retornará um novo token de acesso que pode ser usado para acessar o Microsoft Graph.
1. Obter os dados do Microsoft Graph usando o novo token.
1. Use a serialização de cache de token MSAL.NET cache para armazenar em cache o novo token de acesso para vários, se necessário.

> [!IMPORTANT]
> Como prática recomendada para segurança, sempre use o código do lado do servidor para fazer chamadas do Microsoft Graph ou outras chamadas que exijam a passagem de um token de acesso. Nunca retorne o token OBO ao cliente para permitir que o cliente faça chamadas diretas ao Microsoft Graph. Isso ajuda a proteger o token de ser interceptado ou vazado.

## <a name="known-limitations"></a>Limitações conhecidas

Consentimento do administrador do locatário: uma maneira simples de [consentir](/azure/active-directory/manage-apps/consent-and-permissions-overview#admin-consent) em nome de uma organização como administrador de locatários é obter [o consentimento do administrador](/azure/active-directory/manage-apps/grant-admin-consent).

Você pode solicitar consentimento usando a API de Autenticação. Outra abordagem para obter escopos do Graph é apresentar uma caixa de diálogo de consentimento usando nossa abordagem de autenticação de provedor [OAuth de terceiros existente](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page). Essa abordagem envolve o surgimento de uma caixa de diálogo de consentimento do Azure AD.

<details>
<summary>Para solicitar consentimento adicional usando a API Auth, siga estas etapas:</summary>

1. O token recuperado usando deve `getAuthToken()` ser trocado no lado do servidor usando Azure AD fluxo em nome de para obter [](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) acesso a essas outras APIs do Graph. Certifique-se de usar o ponto de extremidade v2 Graph para esta troca.
2. Se a troca falhar, o Microsoft Azure AD retornará uma exceção de concessão inválida. Normalmente, ele responde com uma das duas mensagens de erro ou `invalid_grant` `interaction_required`.
3. Quando a troca falhar, você deve solicitar consentimento. Use a interface do usuário para solicitar que o usuário do aplicativo conceda outro consentimento. Essa interface do usuário deve incluir um botão que dispara uma caixa Azure AD de consentimento usando [a autenticação silenciosa](~/concepts/authentication/auth-silent-aad.md).
4. Ao solicitar mais consentimento do Azure AD, `prompt=consent` você deve incluir em seu parâmetro [de](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) cadeia de caracteres de consulta para Azure AD, caso contrário, Azure AD não solicitaria outros escopos.
    - Em vez de `?scope={scopes}`, use `?prompt=consent&scope={scopes}`
    - Verifique se `{scopes}` isso inclui todos os escopos que você está solicitando ao usuário, por exemplo, `Mail.Read` ou `User.Read`.
5. Depois que o usuário do aplicativo conceder mais permissões, tente novamente o fluxo OBO para obter acesso a essas outras APIs.

    </details>

## <a name="see-also"></a>Confira também

- [Fluxo on-Behalf-Of do OAuth 2.0](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow)
- [Obter acesso ao MS Graph](/graph/auth-v2-user)
- [Serialização de cache de token no MSAL.NET](/azure/active-directory/develop/msal-net-token-cache-serialization?tabs=aspnet)
- [Provedor MSAL2 do Microsoft Teams](/graph/toolkit/providers/teams-msal2)
