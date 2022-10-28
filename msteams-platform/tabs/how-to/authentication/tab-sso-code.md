---
title: Configuração de código para habilitar o logon único para guias
description: Atualize o código em seu aplicativo de guia para solicitar e receber o token de acesso usando a identidade do Teams do usuário do aplicativo para habilitar o SSO (logon único).
ms.topic: how-to
ms.localizationpriority: high
keywords: guias de autenticação das equipes na API do Graph do Microsoft Azure Active Directory (Azure AD)
ms.openlocfilehash: 20b11032227a08d057a6cdae8e46154004bfdb02
ms.sourcegitcommit: bb15ce26cd65bec90991b703069424ab4b4e1a61
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68772262"
---
# <a name="add-code-to-enable-sso"></a>Adicionar código para habilitar o logon único

Antes de você adicionar código para habilitar o logon único, verifique se você registrou seu aplicativo com o Azure AD.

> [!div class="nextstepaction"]
> [Registrar com o Azure AD](tab-sso-register-aad.md)

Você precisa de configurar seu código do lado do cliente do aplicativo guia para obter um token de acesso do Azure AD. O token de acesso é emitido em nome do aplicativo guia. Se seu aplicativo guia exigir permissões adicionais do Microsoft Graph, você precisará passar o token de acesso para o lado do servidor e trocá-lo por um token do Microsoft Graph.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sso-config-code.png" alt-text="configurar código para lidar com o token de acesso":::

Esta seção cobre:

- [Adicionar código do lado do cliente](#add-client-side-code)
- [Passe o token de acesso para o código ao lado do servidor](#pass-the-access-token-to-server-side-code)
- [Validar o token de acesso](#validate-the-access-token)

## <a name="add-client-side-code"></a>Adicionar código do lado do cliente

Para obter acesso ao aplicativo para o usuário atual do aplicativo, seu código do lado do cliente deve fazer uma chamada ao Teams para obter um token de acesso. Você precisa de atualizar o código do lado do cliente para usar `getAuthToken()` para iniciar o processo de validação.

<br>
<details>
<summary>Saiba mais sobre getAuthToken()</summary>
<br>
`getAuthToken()` é um método de SDK de javaScript do Microsoft Teams. Ele solicita que um token de acesso do Azure AD seja emitido em nome do aplicativo. O token será adquirido do cache, se ele não tiver expirado. Se expirado, uma solicitação é enviada ao Azure AD para obter um novo token de acesso.

 Para obter mais informações, consulte [getAuthToken](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-authentication-getauthtoken&preserve-view=true).
</details>

### <a name="when-to-call-getauthtoken"></a>Quando chamar getAuthToken

Use `getAuthToken()` no momento em que você precisar de token de acesso para o usuário atual do aplicativo:

| Se o token de acesso for necessário... | Chamar getAuthToken()... |
| --- | --- |
| Quando o usuário do aplicativo acessa o aplicativo | Depois de `microsoftTeams.initialize()`. |
| Para usar uma funcionalidade particular do aplicativo | Quando o usuário do aplicativo toma uma ação que requer a assinatura. |

### <a name="add-code-for-getauthtoken"></a>Adicionar código para getAuthToken

Adicionar o trecho de código do JavaScript ao aplicativo guia para:

- Chamar `getAuthToken()`.
- Analisar o token de acesso ou passe-o para o código do lado do servidor.

O seguinte trecho de código mostra um exemplo de chamada `getAuthToken()`.

```javascript
microsoftTeams.initialize();
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Error getting token: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Você pode adicionar chamadas de `getAuthToken()` para todas as funções e manipuladores que iniciam uma ação quando o token é necessário.

<br>
<details>
<summary>Aqui está um exemplo de código do lado do cliente:</summary>

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/config-client-code.png" alt-text="Configurar código do cliente" lightbox="../../../assets/images/authentication/teams-sso-tabs/config-client-code.png":::

</details>

Quando o Teams recebe o token de acesso, ele é armazenado em cache e reutilizado conforme necessário. Este token pode ser usado sempre que `getAuthToken()` for chamado, até ele expirar, sem fazer outra chamada para o Azure AD.

> [!IMPORTANT]
> Como melhores práticas para a segurança do token de acesso:
>
> - Sempre chame `getAuthToken()` quando você precisar de um token de acesso.
> - O Teams armazenará em cache o token de acesso para você. Não o armazene em cache ou no código de seu aplicativo.

### <a name="consent-dialog-for-getting-access-token"></a>Caixa de diálogo de consentimento para obter o token de acesso

Quando você chama `getAuthToken()` e o consentimento do usuário do aplicativo é necessário para permissões no nível do usuário, uma caixa de diálogo do Azure AD é mostrada para o usuário do aplicativo que está conectado no momento.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/tabs-sso-prompt.png" alt-text="Prompt de diálogo de logon único na guia":::

A caixa de diálogo de consentimento que aparece é para escopos de ID aberta definidos no Azure AD. O usuário do aplicativo deve dar consentimento apenas uma vez. Após o consentimento, o usuário do aplicativo pode acessar e usar seu aplicativo guia para as permissões concedidas e escopos.

> [!IMPORTANT]
> Cenários onde as caixas de diálogo de consentimento não são necessárias:
>
> - Se o administrador de locatários tiver concedido consentimento em nome do locatário, os usuários do aplicativo não precisarão ser solicitados a dar consentimento. Isto significa que os usuários do aplicativo não veem as caixas de diálogo de consentimento e podem acessar o aplicativo diretamente.
> - Se seu aplicativo do Microsoft Azure AD estiver registrado no mesmo locatário em que você está fazendo uma solicitação de autenticação no Teams, o usuário do aplicativo não pode ser solicitado a consentir e é concedido um token de acesso imediatamente. Os usuários do anúncio consentem a essas permissões somente se o aplicativo do Azure AD estiver registrado em um locatário diferente.

Se você encontrar qualquer erro, consulte [Solução de problemas de autenticação de logon único no Teams](tab-sso-troubleshooting.md).

### <a name="use-the-access-token-as-an-identity-token"></a>User o token de acesso como um token de identidade

O token devolvido para o aplicativo guia é um token de acesso e um token de ID. O aplicativo guia pode usar o token como um token de acesso para fazer solicitações HTTPS autenticadas para APIs no lado do servidor.

O token de acesso devolvido `getAuthToken()` pode ser usado para estabelecer a identidade de usuário do aplicativo usando as seguintes declarações no token:

- `name`: O nome de exibição do usuário do aplicativo.
- `preferred_username`: O endereço de email do usuário do aplicativo.
- `oid`: Um GUID que representa a ID do usuário do aplicativo.
- `tid`: Um GUID que representa o locatário ao qual o usuário do aplicativo está se conectando.

O Teams pode armazenar em cache esta informação associada à identidade do usuário do aplicativo, tal como as preferências do usuário.

> [!NOTE]
> Se você precisar de construir uma ID única para representar o usuário do aplicativo no seu sistema, consulte [Usando declarações para identificar um usuário de forma confiável](/azure/active-directory/develop/id-tokens#using-claims-to-reliably-identify-a-user-subject-and-object-id).

## <a name="pass-the-access-token-to-server-side-code"></a>Passe o token de acesso para o código ao lado do servidor

Se você precisar acessar as APIs da Web em seu servidor, você precisará passar o token de acesso para seu código do lado do servidor. As APIs da Web devem decodificar o token de acesso para exibir declarações para esse token.

> [!NOTE]
> Se você não receber o Nome de Usuário Principal (UPN) no token de acesso devolvido, adicione-o como uma [declaração opcional](/azure/active-directory/develop/active-directory-optional-claims) no Microsoft Azure AD.
> Para obter mais informações, consulte [Tokens de acesso](/azure/active-directory/develop/access-tokens).

O token de acesso recebido com sucesso pelo `getAuthToken()` fornece acesso (para o usuário autenticado como usuário do aplicativo) às suas APIs da Web. O código ao lado do servidor também pode analisar o token para [informações de identidade](#use-the-access-token-as-an-identity-token), se necessário.

Se você precisar passar o token de acesso para obter dados do Microsoft Graph, consulte [Estender o aplicativo guia com as permissões do Microsoft Graph](tab-sso-graph-api.md).

### <a name="code-for-passing-access-token-to-server-side"></a>Código para passar o token de acesso para o lado do servidor

O código a seguir mostra um exemplo de passagem do token de acesso para o lado do servidor. O token é passado em um `Authorization` cabeçalho ao enviar uma solicitação para uma API da Web do lado do servidor. Este exemplo envia dados JSON, por isso usa o método `POST`. O `GET` é suficiente para enviar o token de acesso quando você não está escrevendo para o servidor.

```javascript
$.ajax({
    type: "POST",
    url: "/api/DoSomething",
    headers: {
        "Authorization": "Bearer " + accessToken
    },
    data: { /* some JSON payload */ },
    contentType: "application/json; charset=utf-8"
}).done(function (data) {
    // Handle success
}).fail(function (error) {
    // Handle error
}).always(function () {
    // Cleanup
});
```

### <a name="validate-the-access-token"></a>Validar o token de acesso

As APIs da Web em seu servidor devem decodificar o token de acesso, e verificar se ele for enviado pelo cliente. O token é um Token Web JSON (JWT) e isso significa que validação funciona como uma validação de token na maioria dos fluxos padrão do OAuth. As APIs da Web devem decodificar o token de acesso. Opcionalmente, você pode copiar e colar o token de acesso manualmente em uma ferramenta, como o jwt.ms.

Há diversas bibliotecas disponíveis que podem lidar com a validação de JWT. A validação básica inclui:

- Verificar se o token foi bem formado
- Verificar se o token foi emitido pela autoridade desejada
- Verificar se o token está direcionado para a API da web

Ao validar o token, lembre-se das seguintes diretrizes:

- Os tokens de logon único válidos são emitidos pelo Azure AD. A declaração `iss` no token deve começar com esse valor.
- O parâmetro do token `aud1` será definido como a ID do aplicativo gerada durante o registro do aplicativo do Azure AD.
- O parâmetro `scp` do token será definido como `access_as_user`.

#### <a name="example-access-token"></a>Token de acesso de exemplo

A seguir está uma carga decodificada típica do token de acesso.

```javascript
{
    aud: "2c3caa80-93f9-425e-8b85-0745f50c0d24",
    iss: "https://login.microsoftonline.com/fec4f964-8bc9-4fac-b972-1c1da35adbcd/v2.0",
    iat: 1521143967,
    nbf: 1521143967,
    exp: 1521147867,
    aio: "ATQAy/8GAAAA0agfnU4DTJUlEqGLisMtBk5q6z+6DB+sgiRjB/Ni73q83y0B86yBHU/WFJnlMQJ8",
    azp: "e4590ed6-62b3-5102-beff-bad2292ab01c",
    azpacr: "0",
    e_exp: 262800,
    name: "Mila Nikolova",
    oid: "6467882c-fdfd-4354-a1ed-4e13f064be25",
    preferred_username: "milan@contoso.com",
    scp: "access_as_user",
    sub: "XkjgWjdmaZ-_xDmhgN1BMP2vL2YOfeVxfPT_o8GRWaw",
    tid: "fec4f964-8bc9-4fac-b972-1c1da35adbcd",
    uti: "MICAQyhrH02ov54bCtIDAA",
    ver: "2.0"
}
```

## <a name="code-samples"></a>Exemplos de código

| Nome do exemplo | Descrição | C#/.NET| Node.js |
|---------------|---------------|------|--------------|
| SSO de guia |Aplicativo de exemplo do Microsoft Teams para SSO de guias do Azure AD| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs) </br>[Kit de ferramentas do Teams](../../../toolkit/visual-studio-code-tab-sso.md)|
| SSO de guia, bot e extensão de mensagem (ME) | Este exemplo mostra o SSO para Tab, Bot e ME – pesquisa, ação, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Atualizar o manifesto do aplicativo do Teams e pré-visualizar o aplicativo](tab-sso-manifest.md)

## <a name="see-also"></a>Confira também

- [jwt.ms](https://jwt.ms/)
- [Declaração opcional do Azure Active Directory](/azure/active-directory/develop/active-directory-optional-claims)
- [Tokens de acesso](/azure/active-directory/develop/access-tokens)
- [Visão geral da Biblioteca de Autenticação da Microsoft (MSAL)](/azure/active-directory/develop/msal-overview)
- [Tokens de iD da plataforma de identidade da Microsoft](/azure/active-directory/develop/id-tokens)
- [Tokens de acesso da plataforma de identidade da Microsoft](/azure/active-directory/develop/access-tokens#validating-tokens)
