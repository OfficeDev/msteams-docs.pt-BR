---
title: Logon Único
description: Descreve o logon único (SSO)
keywords: AAD de autenticação do Microsoft Teams
ms.openlocfilehash: 1857651aecd902f04bd57f5b4e2fb0fda88eb348
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672463"
---
# <a name="single-sign-on"></a>Logon Único

> [!NOTE]
> A API "logon único" atualmente tem suporte somente na _visualização do desenvolvedor_ .

Os usuários entram no Microsoft Teams usando sua conta corporativa ou de estudante (Office 365) e você pode aproveitar isso usando o logon único (SSO) para autorizar o usuário à sua guia do Microsoft Teams. Isso significa que, se um usuário autorizar a usar seu aplicativo na área de trabalho, ele não terá que se resentir em dispositivos móveis e será automaticamente conectado. 

## <a name="how-sso-works-at-runtime"></a>Como o SSO funciona em tempo de execução

O diagrama a seguir mostra como funciona o processo de SSO:

<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. Na guia, JavaScript chama getAuthToken (). Isso informa ao aplicativo Teams para obter um token de autenticação para o aplicativo de guia.
2. Se esta é a primeira vez que o usuário atual usou seu aplicativo de guia, ele será solicitado a confirmar (se o consentimento for necessário) ou se for solicitado a lidar com a autenticação de depuração (como a autenticação de dois fatores).
3. O aplicativo Microsoft Teams solicita o token do aplicativo guia do ponto de extremidade do Azure AD v 1.0 para o usuário atual.
4. O Azure AD envia o token do aplicativo guia para o aplicativo Teams.
5. O aplicativo Microsoft Teams envia o token do aplicativo guia para a guia como parte do objeto de resultado retornado pela chamada getAuthToken ().
6. O JavaScript no aplicativo guia pode analisar o token e extrair as informações necessárias, como o endereço de email do usuário.
    * Observação: esse token só é válido para o envio de um conjunto limitado de APIs de nível de usuário (por exemplo, email, perfil, etc.) e não para escopos de gráfico adicionais (como mail. Read). Consulte nossa seção no final deste documento para obter soluções alternativas sugeridas se você precisar de escopos de gráfico adicionais.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Desenvolver uma guia SSO do Microsoft Teams

Esta seção descreve as tarefas envolvidas na criação de uma guia do Microsoft Teams que usam SSO. Essas tarefas descritas aqui apresentam uma linguagem e uma estrutura de forma agnóstica.

### <a name="1-create-your-aad-application-in-azure"></a>1. criar seu aplicativo AAD no Azure

Registre seu aplicativo no portal de registro para o ponto de extremidade do Azure AD v 1.0. Esse é um processo que leva entre 5 e 10 minutos e inclui as seguintes tarefas:

* Obtendo sua ID de aplicativo do AAD
* Especifique as permissões de que seu aplicativo precisa para o ponto de extremidade do AAD (e, opcionalmente, para o Microsoft Graph). 
* Conceder à área de trabalho do Microsoft Teams, a Web e o aplicativo móvel para confiar no aplicativo
* Preautor o aplicativo Microsoft Teams para seu aplicativo com o nome de escopo `access_as_user`padrão de.

> [!NOTE]
> Há algumas restrições importantes que você deve ter em mente:
>
> * Só damos suporte a permissões de API de gráfico em nível de usuário (IE: email, Profile, offline_access, OpenID. Se você precisar acessar outros escopos de gráfico, leia nossa solução alternativa no final desta documentação.
> * É importante que o nome de domínio do aplicativo seja registrado com seu aplicativo do Azure AD. Este deve ser o mesmo nome de domínio no qual o aplicativo é executado ao solicitar um token de autenticação no Teams e também ao especificar a Propriedade Resource no manifesto do Teams (mais detalhes na próxima seção).
> * No momento, não há suporte para vários domínios por aplicativo
> * Também não há suporte para aplicativos que usam o `azurewebsites.net` domínio, já que esse domínio é muito comum e pode ser um risco de segurança

#### <a name="steps"></a>Etapas

1. Registrar um novo aplicativo no [Azure Active Directory –](https://go.microsoft.com/fwlink/?linkid=2083908) portal de registro de aplicativos
2. Selecione "novo registro". Na página registrar um aplicativo, defina os valores da seguinte maneira:
    * Definir **nome** para o nome do aplicativo
    * Definir **tipos de conta com suporte** para **contas em qualquer diretório organizacional e contas pessoais da Microsoft**
    * Sair do **URI de redirecionamento** vazio
    * Escolha **registrar**
3. Na página Visão geral, copie e salve a **ID do aplicativo (cliente)**. Você precisará dele mais tarde ao atualizar o manifesto do aplicativo do Microsoft Teams.
4. Selecionar **Expor uma API** em **Gerenciar**. Selecione o link **definir** para gerar o URI da ID do aplicativo no formato `api://{AppID}`de. Insira o nome de domínio totalmente qualificado (com uma barra "/" acrescentada ao final) entre as barras duplas de avanço e o GUID. A ID completa deve ter a forma de:`api://fully-qualified-domain-name.com/{AppID}`
    * ex: `api://subdomain.example.com:6789/c6c1f32b-5e55-4997-881a-753cc1d563b7`.

> [!NOTE]
> Se você receber um erro dizendo que o domínio já pertence a alguém, mas você é o seu proprietário, siga o procedimento em [Início Rápido: Adicionar um domínio personalizado ao Azure Active Directory](/azure/active-directory/fundamentals/add-custom-domain) para registrá-lo e, em seguida, repita esta etapa. (Esse erro também pode ocorrer se você não tiver entrado com as credenciais de um administrador no Office 365 locação).

5. Selecione o botão **Adicionar um escopo**. No painel que se abre, insira `access_as_user` como o **Nome de escopo**.
6. Definir quem pode consentir? para administradores e usuários
7. Preencha os campos para configurar os prompts de consentimento de usuário e administrador com os valores que são apropriados `access_as_user` para o escopo. Sugestões:
    * **Título do consentimento do administrador:** O Microsoft Teams pode acessar o perfil do usuário
    * **Descrição do consentimento do administrador**: permite que o Teams chame as APIs Web do aplicativo como o usuário atual.
    * **Título de consentimento do usuário**: o Teams pode acessar seu perfil de usuário e fazer solicitações em seu nome
    * **Descrição do consentimento do usuário:** Habilitar o Teams para chamar as APIs deste aplicativo com os mesmos direitos
8. Verifique se o **estado** está definido como **habilitado**
9. Selecionar **Adicionar escopo**
    * Observação: a parte de domínio do **nome do escopo** exibida logo abaixo do campo de texto deve corresponder automaticamente ao conjunto de URI da **ID do aplicativo** na `/access_as_user` etapa anterior, com acrescentado ao final; por exemplo: 
        * `api://subdomain.example.com:6789/c6c1f32b-5e55-4997-881a-753cc1d563b7/access_as_user`
10. Na seção **aplicativos cliente autorizados** , identifique os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo. Cada uma das seguintes IDs precisa ser inserida:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264`(Aplicativo móvel/aplicativo de área de trabalho do Microsoft Teams)
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346`(Aplicativo Web do Teams)
11. Navegue até **permissões de API**e certifique-se de adicionar as permissões a seguir:
    * User. Read (ativado por padrão)
    * email
    * offline_access
    * openid
    * perfil

### <a name="2-update-your-microsoft-teams-application-manifest"></a>2. atualize seu manifesto de aplicativo do Microsoft Teams

Adicione novas propriedades ao manifesto do Microsoft Teams:

* **WebApplicationInfo** – o pai dos seguintes elementos.
* **ID** – a ID do cliente do aplicativo. Esta é uma ID de aplicativo que você obtém como parte do registro do aplicativo com o ponto de extremidade do Azure AD 1,0.
* **Resource** -o domínio e o subdomínio do aplicativo. Este é o mesmo URI (incluindo o `api://` protocolo) que você usou ao registrar o aplicativo no AAD. A parte de domínio desse URI deve corresponder ao domínio, incluindo todos os subdomínios, usados nas URLs na seção do manifesto do aplicativo do Microsoft Teams.

```json
"webApplicationInfo": {
  "id": "<application_GUID here>",
  "resource": "<web_API resource here>"
}
```

Observações:

* O recurso para um aplicativo AAD normalmente será a raiz da URL do site e a appID (por exemplo, `api://subdomain.example.com/6789/c6c1f32b-5e55-4997-881a-753cc1d563b7`). Também utilizamos esse valor para garantir que sua solicitação seja proveniente do mesmo domínio. Therefor certifique-se de `contentURL` que seu para sua guia usa os mesmos domínios de sua Propriedade Resource.
* Você precisa estar usando o manifesto versão 1,5 ou superior para que esses campos sejam usados.
* Escopos não são suportados no manifesto e, em vez disso, devem ser especificados na seção permissões de API no portal do Azure

### <a name="3-get-an-authentication-token-from-your-client-side-code"></a>3. Obtenha um token de autenticação do seu código do lado do cliente

Veja a aparência da API de autenticação:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); },
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Quando você chama `getAuthToken` e o consentimento do usuário adicional é necessário (para permissões no nível do usuário), mostraremos uma caixa de diálogo para o usuário incentivando-o a conceder consentimento adicional. 

<img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>

## <a name="demo-code"></a>Código de demonstração

Por ora, você pode visitar nossa tarefa de aplicativo de teste [Meow](https://github.com/ydogandjiev/taskmeow) e usar o manifesto de `teams.auth.service.js` SSO `sso.auth.service.js` e fazer checkout do arquivo e do para ver como lidamos com o fluxo de trabalho de autenticação.

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="apps-that-require-additional-graph-scopes"></a>Aplicativos que exigem escopos de gráfico adicionais

Nossa implementação atual do SSO concede consentimento apenas para permissões de nível de usuário (email, perfil, offline_access, OpenID), mas não para outras APIs (como mail. Read). Se seu aplicativo precisar de escopos de gráficos adicionais, há algumas soluções alternativas para habilitar isso.

#### <a name="tenant-admin-consent"></a>Consentimento do administrador do locatário

A abordagem mais simples seria fazer com que um administrador de locatários se consentisse em nome da organização. Isso significa que os usuários não terão que se concordar com esses escopos e você poderá ficar livre para trocar o lado do servidor de token usando o [fluxo em nome de do](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)AAD. Essa solução alternativa é aceitável para aplicativos de linha de negócios internos, mas pode não ser suficiente para ISVs que podem não confiar na aprovação do administrador de locatários.

Uma maneira simples de conenviar em nome de uma organização (como um administrador de locatários) é visitar:

* `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>`

#### <a name="asking-for-additional-consent-using-the-auth-api"></a>Solicitar consentimento adicional usando a API de autenticação

Outra abordagem para obter escopos de gráfico adicionais seria apresentar uma caixa de diálogo de consentimento usando nossa [abordagem existente de autenticação AAD baseada na Web,](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) que envolve a apresentação de uma caixa de diálogo de consentimento do AAD. Há algumas adições notáveis:

1. O token recuperado usando getAuthToken precisaria ser trocado no servidor usando o [fluxo em nome de](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow) AADs para obter acesso a essas APIs adicionais do Graph.
    * Certifique-se de usar o ponto de extremidade do gráfico v2 para esta troca
2. Se o Exchange falhar, o AAD retornará uma exceção de concessão inválida. Há geralmente uma de duas mensagens de erro: `ConsentRequired` ou`InteractionRequired`
3. Quando o Exchange falhar, você precisará solicitar o consentimento adicional. Recomendamos que você mostre algumas interfaces de usuário solicitando que o usuário conceda um consentimento adicional. Esta interface do usuário deve incluir um botão que dispare uma caixa de diálogo de consentimento do AAD usando nossa [API de autenticação AAD](~/concepts/authentication/auth-silent-aad.md).
4. Ao solicitar o consentimento adicional do AAD, você precisa incluir `prompt=consent` em seu parâmetro de cadeia de caracteres de [consulta](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) para AAD caso contrário, o AAD não solicitará os escopos adicionais.
    * Em vez de:`?scope={scopes}`
    * Use:`?prompt=consent&scope={scopes}`
    * Certifique-se `{scopes}` de incluir todos os escopos para os quais você está solicitando o usuário (ex: mail. Read ou User. Read).
5. Depois que o usuário tiver concedido permissão adicional, repita o em em nome de fluxo para obter acesso a essas APIs adicionais.

### <a name="non-aad-authentication"></a>Autenticação não AAD

A solução de autenticação descrita acima só funciona para aplicativos e serviços que dão suporte ao Azure AD como um provedor de identidade. Os aplicativos que desejam autenticar usando serviços baseados em AAD precisam continuar usando o fluxo de [autenticação da Web](~/concepts/authentication.md)baseado em pop-up.
