---
title: Suporte de login único para guias
description: Descreve o SSO (logon único)
ms.topic: how-to
ms.localizationpriority: high
keywords: api de logon único de autenticação de equipes SSO do Microsoft Azure Active Directory (Azure AD)
ms.openlocfilehash: edd7e08167c0efb93b7a578de12b7e1873aa193f
ms.sourcegitcommit: b9af51e24c9befcf46945400789e750c34723e56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62821721"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>Suporte ao SSO (logon único) para guias

Os usuários do Microsoft Teams que entram em sua conta corporativa, de estudante ou conta Microsoft que seja Office 365, Outlook, poderão aproveitar os benefícios permitindo que um único login autorize sua guia Teams ou módulo de tarefa em clientes móveis ou de desktop. Se um usuário entrar um vez, não precisará entrar novamente em outro dispositivo, pois será conectado automaticamente. Além disso, seu token de acesso é pré-buscado para melhorar o desempenho e os tempos de carregamento.

> [!NOTE]
> **versões do cliente móvel do Teams compatíveis com SSO**  
>
> ✔Teams para Android (1416/1.0.0.2020073101 e posterior)
>
> ✔Teams para iOS (_Versão_: 2.0.18 e posterior)  
> 
> ✔SDK do JavaScript do Teams (_Versão_: 1.10 e posterior) para que o SSO funcione no painel lateral da reunião. 
>
> Para obter uma melhor experiência no Teams, use a versão mais recente do iOS e Android.

> [!NOTE]
> **Início rápido**  
>
> O caminho mais simples para começar com o SSO da guia é com o kit de ferramentas do Teams para o Microsoft Visual Studio Code. Para obter mais informações, confira [SSO com kit de ferramentas do Teams e Visual Studio Code para guias](../../../toolkit/visual-studio-code-tab-sso.md)

## <a name="how-sso-works-at-runtime"></a>Como o SSO funciona em tempo de execução

A imagem a seguir mostra como o processo de SSO funciona:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. Na guia, uma chamada JavaScript é feita para `getAuthToken()`. `getAuthToken()` informa ao Teams para obter um token de acesso para o aplicativo de guia.
2. Se o usuário atual estiver usando seu aplicativo de guia pela primeira vez, haverá uma solicitação de permissão se o consentimento for necessário. Como alternativa, haverá uma solicitação para lidar com a autenticação step-up, como a autenticação de dois fatores.
3. O Teams solicita o token de acesso à guia do ponto de extremidade do Microsoft Azure AD para o usuário atual.
4. O Microsoft Azure AD envia o token de acesso à guia para o aplicativo Teams.
5. O Teams envia o token de acesso à guia para a guia como parte do objeto de resultado retornado pela chamada `getAuthToken()`.
6. O token é analisado no aplicativo de guia usando JavaScript para extrair as informações necessárias, como o endereço de email do usuário.

> [!NOTE]
> O `getAuthToken()` é válido apenas para permitir um conjunto limitado de APIs a nível de usuário que são email, perfil, offline_access e OpenId. Ele não é usado para escopos Graph como `User.Read` ou `Mail.Read`. Para obter soluções alternativas sugeridas, confira [Obter um token com permissões do Graph](#get-an-access-token-with-graph-permissions).

A API do SSO também funciona em [módulos de tarefas](../../../task-modules-and-cards/what-are-task-modules.md) que incorporam conteúdo da Web.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Desenvolver uma guia de SSO do Microsoft Teams

Esta seção descreve as tarefas envolvidas na criação de uma guia do Teams que usa SSO. Essas tarefas possuem uma linguagem e estrutura desconhecida.

### <a name="1-create-your-azure-ad-application"></a>1. Criar seu aplicativo do Microsoft Azure AD

> [!NOTE]
> Há algumas restrições importantes que você deve conhecer:
>
> * Há suporte apenas para API do Graph a nível de usuário, ou seja, email, perfil, offline_access, OpenId. Se você precisa ter acesso a outros escopos do Graph, como `User.Read` ou `Mail.Read`, confira [Obter um token de acesso com permissões do Graph](#get-an-access-token-with-graph-permissions).
> * É importante que o nome de domínio do aplicativo seja o mesmo que o nome de domínio que você registrou para seu aplicativo do Microsoft Azure AD.
> * Atualmente, não há suporte para vários domínios por aplicativo.
> * O usuário deve definir `accessTokenAcceptedVersion` como `2` para um novo aplicativo.

**Para registrar seu aplicativo por meio do portal do Microsoft Azure AD**

1. Registre um novo aplicativo no portal [Registros de aplicativo Microsoft Azure AD](https://go.microsoft.com/fwlink/?linkid=2083908).
1. Selecione **Novo registro**. A página **Registrar um aplicativo** é exibida.
1. Na página **Registrar um aplicativo**, insira os seguintes valores:
    1. Insira um **Nome** para seu aplicativo.
    2. Escolha os **tipos de conta compatíveis**, selecione locatário único ou tipo de conta multilocatário. ¹
    * Deixe o **URI de Redirecionamento** vazio.
    3. Escolha **Registrar**.
1. Na página de visão geral, copie e salve a **ID do aplicativo (cliente).** Você o terá mais tarde ao atualizar seu manifesto do aplicativo Teams.
1. Em **Gerenciar**, selecione **Expor uma API**.

    > [!NOTE]
    > Se você estiver criando um aplicativo com um bot e uma guia, insira o URI de ID do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}`.

1. Selecione o link **Definir** para gerar o URI de ID do Aplicativo no formato de `api://{AppID}`. Insira o nome de domínio totalmente qualificado com uma barra "/" acrescentada ao final entre as duas barras e o GUID. A ID inteira deve ter a forma de `api://fully-qualified-domain-name.com/{AppID}`. ² Por exemplo, `api://subdomain.example.com/00000000-0000-0000-0000-000000000000`. O nome de domínio totalmente qualificado é o nome de domínio em formato legível por humanos a partir do qual seu aplicativo é distribuído. Se você estiver usando um serviço de túnel, como ngrok, deverá atualizar esse valor sempre que o subdomínio ngrok mudar.
1. Selecione **Adicionar um escopo**. No painel que se abre, insira **access_as_user** como o **Nome de escopo**.
1. Na caixa **Quem pode dar consentimento?** insira **Administradores e usuários**.
1. Insira os detalhes nas caixas para configurar as solicitações de consentimento do administrador e do usuário com valores apropriados para o escopo `access_as_user`:
    * **Título de consentimento do administrador:** Teams pode acessar o perfil do usuário.
    * **Descrição de consentimento do administrador**: o Teams pode chamar as APIs da web do aplicativo como o usuário atual.
    * **Título de consentimento do usuário**: o Teams pode acessar seu perfil e fazer solicitações em seu nome.
    * **Descrição de consentimento do usuário:** o Teams pode chamar as APIs deste aplicativo com os mesmos direitos que você tem.
1. Verifique se o **Estado** está definido como **Habilitado**.
1. Selecione **Adicionar escopo** para salvar os detalhes. A parte de domínio do **Nome de escopo** exibidos abaixo do campo de texto deve corresponder automaticamente ao URI de **ID do aplicativo** definidos na etapa anterior com `/access_as_user` acrescentado ao final `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user`.
1. Na seção **Aplicativos cliente autorizados,** identifique os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo. Selecione **Adicionar um aplicativo cliente**. Insira cada uma das seguintes IDs de cliente e selecione o escopo autorizado criado na etapa anterior:
    * Aplicativo da área de trabalho ou móvel `1fec8e78-bce4-4aaf-ab1b-5451cc387264` para Teams.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` para aplicativo web do Teams.
1. Acesse **Permissões de API**. Selecione **Adicionar uma permissão** > **Microsoft Graph** > **Permissões delegadas**, em seguida, adicione as seguintes permissões de API do Graph:
    * User.Read habilitado por padrão
    * email
    * offline_access
    * OpenId
    * perfil

1. Acesse **Autenticação**.

    > [!IMPORTANT]
    > Se um aplicativo não tiver tido o consentimento do administrador de IT, os usuários terão que fornecer consentimento na primeira vez que usarem um aplicativo.

    Para inserir um URI de redirecionamento:
    * Selecione **Adicionar uma plataforma**.
    * Selecione **Web**.
    * Insira o **URI de redirecionamento** para seu aplicativo. Esse URI é o mesmo nome de domínio totalmente qualificado inserido na etapa 5. Ele também é seguido pela rota da API para a qual uma resposta de autenticação é enviada. Se você estiver seguindo qualquer uma das amostras do Teams, o URI será `https://subdomain.example.com/auth-end`. Para obter mais informações, confira [Fluxo de código de autorização OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

    > [!NOTE]
    > A concessão implícita não é necessária para o SSO de guia.

Parabéns! Você concluiu os pré-requisitos de registro do aplicativo para continuar com seu aplicativo de SSO de guia.

> [!NOTE]
>
> * ¹ Se seu aplicativo do Microsoft Azure AD estiver registrado no mesmo locatário em que você está fazendo uma solicitação de autenticação no Teams, o usuário não poderá ser solicitado a consentir e receberá um token de acesso imediatamente. Os usuários só consentem com essas permissões se o aplicativo do Microsoft Azure AD estiver registrado em um locatário diferente.
> * ² Se o domínio personalizado não for adicionado ao Microsoft Azure AD, você receberá um erro informando que o nome do host não deve ser baseado em um domínio já pertencente. Para adicionar um domínio personalizado ao Microsoft Azure AD e registrá-lo, siga o procedimento [adicione um nome de domínio personalizado ao Microsoft Azure AD](/azure/active-directory/fundamentals/add-custom-domain) e repita a etapa 5. Você também verá esse erro se você não estiver conectado com as credenciais do administrador no locatário do Office 365.
> * Se você não estiver recebendo o nome UPN no token de acesso retornado, poderá adicioná-lo como uma [declaração opcional](/azure/active-directory/develop/active-directory-optional-claims) no Microsoft Azure AD.

### <a name="2-update-your-teams-application-manifest"></a>2. Atualize seu manifesto do aplicativo Teams

Use o código a seguir para adicionar novas propriedades ao manifesto Teams:

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

* **WebApplicationInfo** é o pai dos seguintes elementos:

> [!div class="checklist"]
> * **id** - A ID do cliente do aplicativo. Esta é a ID do aplicativo que você obteve como parte do registro do aplicativo no Azure AD.
>* **resource** - O domínio e o subdomínio do seu aplicativo. Esse é o mesmo URI (incluindo o protocolo `api://`) que você registrou ao criar seu `scope` na etapa 6. Você não deve incluir o caminho `access_as_user` em seu recurso. Parte de domínio deste URI deve coincidir com o domínio, incluindo qualquer subdomínio, usado nas URLs do manifesto do aplicativo Teams.

> [!NOTE]
>
>* O recurso para um aplicativo do Microsoft Azure AD geralmente é a raiz de sua URL de site e a appID (por exemplo, `api://subdomain.example.com/00000000-0000-0000-0000-000000000000`). Esse valor também é usado para garantir que sua solicitação venha do mesmo domínio. Verifique se `contentURL` para sua guia usa os mesmos domínios que sua propriedade de recurso.
>* Você deve usar o manifesto versão 1.5 ou superior para implementar o campo `webApplicationInfo`.

### <a name="3-get-an-access-token-from-your-client-side-code"></a>3. Obter um token de acesso do código do lado do cliente

Use a seguinte API de autenticação:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Quando você chama `getAuthToken` e o consentimento do usuário é necessário para permissões no nível do usuário, uma caixa de diálogo é exibida para o usuário conceder consentimento.

Depois de receber o token de acesso no retorno de chamada de sucesso, decodifique o token de acesso para exibir declarações desse token. Opcionalmente, copie e cole manualmente o token de acesso em uma ferramenta, como [jwt.ms](https://jwt.ms/). Se você não estiver recebendo o UPN no token de acesso retornado, adicione-o como uma [declaração opcional](/azure/active-directory/develop/active-directory-optional-claims) no Microsoft Azure AD. Para obter mais informações, confira [tokens de acesso](/azure/active-directory/develop/access-tokens).

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="code-snippets"></a>Trechos de código

O código a seguir fornece um exemplo de fluxo On-Behalf-Of para buscar o token de acesso usando a biblioteca MSAL:

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

```javascript

// Exchange cliend side token with server token
  app.post('/getProfileOnBehalfOf', function(req, res) {
        var tid = < "Tenand id" >
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

## <a name="code-sample"></a>Exemplo de código

|**Nome de exemplo**|**Descrição**|**C#**|**Node.js**|
|---------------|---------------|------|--------------|
| SSO de guia |Aplicativo de exemplo do Microsoft Teams para SSO de guias do Azure AD| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs) </br>[Kit de ferramentas do Teams](../../../toolkit/visual-studio-code-tab-sso.md)|

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="get-an-access-token-with-graph-permissions"></a>Obter um token de acesso com permissões do Graph

Nossa implementação atual para o SSO concede consentimento apenas para permissões no nível do usuário que não são usáveis para fazer chamadas do Graph. Para obter as permissões (escopos) necessárias para fazer uma chamada do Graph, as soluções de SSO devem implementar um serviço Web personalizado para trocar o token recebido do SDK do JavaScript do Teams para um token que inclua os escopos necessários. Isso é feito usando o [fluxo On-Behalf-Of](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow) do Microsoft Azure AD.

### <a name="tenant-admin-consent"></a>Consentimento do administrador do locatário

Uma maneira simples de consentir em nome de uma organização como administrador de locatário é fazer referência a `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>`.

#### <a name="ask-for-consent-using-the-auth-api"></a>Solicitar consentimento usando a API Auth

Outra abordagem para obter escopos do Graph é apresentar uma caixa de diálogo de consentimento usando nossa [abordagem de autenticação do Azure AD baseada na Web](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page) existente. Essa abordagem envolve o surgimento de uma caixa de diálogo de consentimento do Azure AD.

**Para solicitar consentimento adicional usando a API Auth**

1. O token recuperado usando `getAuthToken()` deve ser trocado no lado do servidor usando o [fluxo On-Behalf-Of](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) do Microsoft Azure AD para obter acesso a essas outras APIs do Graph. Certifique-se de usar o ponto de extremidade v2 Graph para esta troca.
2. Se a troca falhar, o Microsoft Azure AD retornará uma exceção de concessão inválida. Geralmente, há uma das duas mensagens de erro, `invalid_grant` ou `interaction_required`.
3. Quando a troca falhar, você deve solicitar consentimento. Exiba uma interface do usuário (UI) solicitando que o usuário conceda outro consentimento. Essa interface do usuário deve incluir um botão que dispare uma caixa de diálogo de consentimento do Microsoft Azure AD usando nosso [ API de autenticação do Microsoft Azure AD](~/concepts/authentication/auth-silent-aad.md).
4. Ao solicitar mais consentimento do Microsoft Azure AD, você deve incluir `prompt=consent` em seu [parâmetro cadeia de caracteres de consulta](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) no Azure AD, caso contrário, o Microsoft Azure AD não solicitará os outros escopos.
    * Em vez de `?scope={scopes}`
    * Use esse `?prompt=consent&scope={scopes}`
    * Verifique se `{scopes}` inclui todos os escopos que você está solicitando ao usuário, por exemplo, Mail.Read ou User.Read.
5. Depois que o usuário tiver concedido mais permissão, repita o fluxo On-Behalf-Of para obter acesso a essas outras APIs.

### <a name="non-azure-ad-authentication"></a>Autenticação não Microsoft Azure AD

A solução de autenticação descrita acima só funciona para aplicativos e serviços que dão suporte ao Microsoft Azure AD como um provedor de identidade. Os aplicativos que desejam autenticar usando serviços não baseados no Microsoft Azure AD devem continuar usando o [fluxo de autenticação da web](~/concepts/authentication.md).

> [!NOTE]
> O SSO tem suporte para aplicativos de propriedade do cliente dentro dos locatários B2C do Microsoft Azure AD.

## <a name="step-by-step-guides"></a>Guias passo a passo

* Siga o [guia passo a passo](../../../sbs-tabs-and-messaging-extensions-with-sso.yml) para autenticar extensões de mensagens e guias.
* Siga o [guia passo a passo](../../../sbs-tab-with-adaptive-cards.yml) para criar guia com cartões adaptáveis.

## <a name="see-also"></a>Confira também
[Teams Bot com logon único](../../../sbs-bots-with-sso.yml)
