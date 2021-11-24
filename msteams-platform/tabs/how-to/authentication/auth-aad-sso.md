---
title: Suporte de login único para guias
description: Descreve o SSO (sign-on único)
ms.topic: how-to
ms.localizationpriority: medium
keywords: SSO de autenticação do teams AAD api de login único
ms.openlocfilehash: 96916d526dba7a6ff7b019fb070b53943b3c216c
ms.sourcegitcommit: 345d713a680c0e0978d7f82c0330c1fd0d6b3e7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2021
ms.locfileid: "61151894"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>Suporte a SSO (login único) para guias

Os usuários Microsoft Teams entrar em sua conta de trabalho, escola ou Microsoft que seja Office 365, Outlook, você pode aproveitar a vantagem permitindo que um único login autorize sua guia Teams ou módulo de tarefa em clientes desktop ou móveis. Se um usuário entrar uma vez, ele não precisa entrar novamente em outro dispositivo quando estiver conectado automaticamente. Além disso, seu token de acesso é pré-buscado para melhorar o desempenho e os tempos de carregamento.

> [!NOTE]
> **Teams versões do cliente móvel que suportam o SSO**  
>
> ✔Teams para Android (1416/1.0.0.2020073101 e posterior)
>
> ✔Teams para iOS (_Versão_: 2.0.18 e posterior)  
> 
> ✔Teams SDK JavaScript (_Versão_: 1.10 e posterior) para que o SSO funcione no painel do lado da reunião. 
>
> Para ter a melhor experiência com Teams, use a versão mais recente do iOS e android.

> [!NOTE]
> **Início rápido**  
>
> O caminho mais simples para começar com a guia SSO é com o Teams de ferramentas para Visual Studio Code. Para obter mais informações, consulte [SSO with Teams toolkit and Visual Studio Code for tabs](../../../toolkit/visual-studio-code-tab-sso.md)

## <a name="how-sso-works-at-runtime"></a>Como o SSO funciona em tempo de execução

A imagem a seguir mostra como o processo de SSO funciona:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. Na guia, uma chamada JavaScript é feita para `getAuthToken()`. `getAuthToken()`informa Teams obter um token de acesso para o aplicativo de tabulação.
2. Se o usuário atual estiver usando seu aplicativo de tabulação pela primeira vez, haverá um prompt de solicitação para consentir se o consentimento for necessário. Como alternativa, há um prompt de solicitação para lidar com a autenticação de etapa, como a autenticação de dois fatores.
3. Teams solicita o token de acesso de tabulação do ponto de extremidade Azure Active Directory (AAD) para o usuário atual.
4. AAD envia o token de acesso de tabulação para o Teams aplicativo.
5. Teams envia o token de acesso de tabulação para a guia como parte do objeto de resultado retornado pela `getAuthToken()` chamada.
6. O token é analisado no aplicativo de tabulação usando JavaScript, para extrair informações necessárias, como o endereço de email do usuário.

> [!NOTE]
> O é válido apenas para consentir um conjunto limitado de APIs no nível do usuário que são `getAuthToken()` email, perfil, offline_access e OpenId. Ele não é usado para escopos Graph como `User.Read` ou `Mail.Read` . Para obter soluções alternativas sugeridas, consulte [Obter um token de acesso com Graph permissões](#get-an-access-token-with-graph-permissions).

A API do SSO também funciona em [módulos de tarefas](../../../task-modules-and-cards/what-are-task-modules.md) que incorporam conteúdo da Web.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Desenvolver uma guia Microsoft Teams SSO

Esta seção descreve as tarefas envolvidas na criação de uma guia Teams que usa SSO. Essas tarefas são agnósticas de idioma e estrutura.

### <a name="1-create-your-aad-application"></a>1. Crie seu aplicativo AAD aplicativo

**Para registrar seu aplicativo na visão [geral AAD portal](https://azure.microsoft.com/features/azure-portal/)**

1. Obter sua [AAD ID do aplicativo.](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in) 
1. Especifique as permissões que seu aplicativo precisa para o ponto de extremidade AAD e, opcionalmente, Graph.
1. [Conceda permissões](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) para Teams desktop, web e aplicativos móveis.
1. Pré-autorizar Teams selecionando o botão **Adicionar** um escopo e, no painel que é aberto, insira access_as_user **como** o nome do **escopo**.

> [!NOTE]
> Há algumas restrições importantes que você deve saber:
>
> * Há suporte apenas para Graph de API no nível do usuário, ou seja, email, perfil, offline_access, OpenId. Se você deve ter acesso a outros escopos Graph, como ou , consulte Obter um token de acesso com Graph `User.Read` `Mail.Read` [permissões](#get-an-access-token-with-graph-permissions).
> * É importante que o nome de domínio do aplicativo seja o mesmo que o nome de domínio que você registrou para seu AAD aplicativo.
> * Atualmente, não há suporte para vários domínios por aplicativo.
> * O usuário deve definir `accessTokenAcceptedVersion` como para um novo `2` aplicativo.

**Para registrar seu aplicativo por meio do AAD portal**

1. Registre um novo aplicativo no portal [AAD Registros de Aplicativos.](https://go.microsoft.com/fwlink/?linkid=2083908)
1. Selecione **Novo Registro**. A **página Registrar um aplicativo** é exibida.
1. Na página **Registrar um aplicativo,** insira os seguintes valores:
    1. Insira um **Nome** para seu aplicativo.
    2. Escolha os **tipos de conta com** suporte, selecione locatário único ou tipo de conta multitenant. ¹
    * Deixe o **URI de Redirecionamento** vazio.
    3. Escolha **Registrar**.
1. Na página visão geral, copie e salve a **ID do aplicativo (cliente).** Você deve tê-lo mais tarde ao atualizar seu manifesto Teams aplicativo.
1. Em **Gerenciar**, selecione **Expor uma API**.

    > [!NOTE]
    > Se você estiver criando um aplicativo com um bot e uma guia, insira o URI de ID do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

1. Selecione o link **Definir** para gerar o URI de ID do Aplicativo no formato `api://{AppID}` de . Insira seu nome de domínio totalmente qualificado com uma barra de avanço "/" anexada ao final, entre as barras de avanço duplo e o GUID. A ID inteira deve ter a forma `api://fully-qualified-domain-name.com/{AppID}` de . ² Por exemplo, `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` . O nome de domínio totalmente qualificado é o nome de domínio acessível para humanos a partir do qual seu aplicativo é servido. Se você estiver usando um serviço de tunelamento, como ngrok, deverá atualizar esse valor sempre que o subdomínio ngrok mudar.
1. Selecione **Adicionar um escopo**. No painel que é aberto, digite **access_as_user** como o **nome do escopo**.
1. Na caixa **Who pode consentir?** digite **Administradores e usuários**.
1. Insira os detalhes nas caixas para configurar os prompts de consentimento do administrador e do usuário com valores apropriados para o `access_as_user` escopo:
    * **Título de consentimento do administrador:** Teams pode acessar o perfil do usuário.
    * **Descrição do** consentimento do administrador : Teams pode chamar as APIs web do aplicativo como o usuário atual.
    * **Título de consentimento do** usuário : Teams pode acessar seu perfil e fazer solicitações em seu nome.
    * **Descrição do consentimento** do usuário: Teams pode chamar as APIs desse aplicativo com os mesmos direitos que você tem.
1. Verifique se o **Estado** está definido como **Habilitado**.
1. Selecione **Adicionar escopo** para salvar os detalhes. A parte de domínio do nome **escopo** exibida abaixo do campo de texto deve corresponder automaticamente ao conjunto de URI **de ID** do aplicativo na etapa anterior, com anexado `/access_as_user` ao final `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user` .
1. Na seção **Aplicativos cliente autorizados,** identifique os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo. Selecione **Adicionar um aplicativo cliente**. Insira cada uma das seguintes IDs de cliente e selecione o escopo autorizado criado na etapa anterior:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264`para Teams aplicativo móvel ou desktop.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346`para Teams web.
1. Navegue até **Permissões de API**. Selecione **Adicionar uma permissão microsoft**  >  **Graph** permissões  >  **delegadas**, em seguida, adicione as seguintes permissões de Graph API:
    * User.Read habilitado por padrão
    * email
    * offline_access
    * OpenId
    * perfil

1. Navegue até **Autenticação**.

    > [!IMPORTANT]
    > Se um aplicativo não tiver sido concedido o consentimento do administrador de IT, os usuários terão que fornecer consentimento na primeira vez que usarem um aplicativo.

    Para inserir um URI de redirecionamento:
    * Selecione **Adicionar uma plataforma**.
    * Selecione **Web**.
    * Insira o **URI de redirecionamento** para seu aplicativo. Esse URI é o mesmo nome de domínio totalmente qualificado inserido na etapa 5. Ele também é seguido pela rota da API para a qual uma resposta de autenticação é enviada. Se você estiver seguindo qualquer uma das amostras Teams, o URI será `https://subdomain.example.com/auth-end` . Para obter mais informações, consulte [OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

    > [!NOTE]
    > A concessão implícita não é necessária para o SSO da guia.

Parabéns! Você concluiu os pré-requisitos de registro do aplicativo para continuar com seu aplicativo SSO de guia.

> [!NOTE]
>
> * ¹ Se seu aplicativo AAD estiver registrado no mesmo locatário em que você está fazendo uma solicitação de autenticação no Teams, o usuário não pode ser solicitado a consentir e é concedido um token de acesso imediatamente. Os usuários só consentem com essas permissões se o aplicativo AAD estiver registrado em um locatário diferente.
> * ² Se o domínio personalizado não for adicionado ao AAD, você receberá um erro informando que o nome do host não deve se basear em um domínio já pertencente. Para adicionar domínio personalizado AAD e registrá-lo, siga o procedimento adicionar um nome de domínio personalizado ao AAD e repita [a](/azure/active-directory/fundamentals/add-custom-domain) etapa 5. Você também poderá obter esse erro se não estiver se inscreveu com credenciais de administrador no Office 365 de adoção.
> * Se você não estiver recebendo o nome principal do usuário (UPN) no token de acesso retornado, poderá adicioná-lo como uma declaração opcional [no](/azure/active-directory/develop/active-directory-optional-claims) AAD.

### <a name="2-update-your-teams-application-manifest"></a>2. Atualize seu manifesto Teams aplicativo

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
>* **resource** - O domínio e o subdomínio do seu aplicativo. Esse é o mesmo URI (incluindo o `api://` protocolo) que você registrou ao criar seu `scope` na etapa 6. Você não deve incluir o `access_as_user` caminho em seu recurso. A parte de domínio deste URI deve corresponder ao domínio, incluindo quaisquer subdomas, usados nas URLs do manifesto do Teams aplicativo.

> [!NOTE]
>
>* O recurso para um AAD app geralmente é a raiz de sua URL de site e o appID (por `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` exemplo, ). Esse valor também é usado para garantir que sua solicitação seja proveniente do mesmo domínio. Verifique se a `contentURL` guia para sua guia usa os mesmos domínios que sua propriedade de recurso.
>* Você deve usar o manifesto versão 1.5 ou superior para implementar o `webApplicationInfo` campo.

### <a name="3-get-an-access-token-from-your-client-side-code"></a>3. Obter um token de acesso do código do lado do cliente

Use a seguinte API de autenticação:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Quando você chama e o consentimento do usuário é necessário para permissões no nível do usuário, uma caixa de diálogo é mostrada para o `getAuthToken` usuário conceder consentimento.

Depois de receber o token de acesso no retorno de chamada de sucesso, decodificar o token de acesso para exibir declarações desse token. Opcionalmente, copie manualmente e colar o token de acesso em uma ferramenta, como jwt.ms [.](https://jwt.ms/) Se você não estiver recebendo o UPN no token de acesso retornado, adicione-o como uma declaração [opcional](/azure/active-directory/develop/active-directory-optional-claims) no AAD. Para obter mais informações, consulte [tokens de acesso](/azure/active-directory/develop/access-tokens).

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="code-sample"></a>Exemplo de código

|**Nome do exemplo**|**Descrição**|**C#**|**Node.js**|
|---------------|---------------|------|--------------|
| Guia SSO |Microsoft Teams exemplo de aplicativo para guias do Azure AD SSO| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs), </br>[Teams Toolkit](../../../toolkit/visual-studio-code-tab-sso.md)|

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="get-an-access-token-with-graph-permissions"></a>Obter um token de acesso com Graph permissões

Nossa implementação atual para o SSO concede consentimento apenas para permissões no nível do usuário que não são usáveis para fazer Graph chamadas. Para obter as permissões (escopos) necessárias para fazer uma chamada Graph, as soluções de SSO devem implementar um serviço Web personalizado para trocar o token que recebeu do SDK javascript do Teams para um token que inclua os escopos necessários. Isso é feito AAD [fluxo em nome do AAD.](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)

#### <a name="tenant-admin-consent"></a>Consentimento do administrador do locatário

Uma maneira simples de consentir em nome de uma organização como administrador de locatário é fazer referência a `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>` .

#### <a name="ask-for-consent-using-the-auth-api"></a>Solicitar consentimento usando a API Auth

Outra abordagem para obter Graph escopos é apresentar uma caixa de diálogo de consentimento usando nossa abordagem de autenticação do [Azure AD](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page)baseada na Web existente. Essa abordagem envolve a aparecendo uma caixa de diálogo de consentimento do Azure AD.

**Para solicitar consentimento adicional usando a API Auth**

1. O token recuperado usando deve ser trocado no lado do servidor usando AAD fluxo em nome do usuário para obter acesso às outras `getAuthToken()` APIs Graph. [](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) Certifique-se de usar o ponto de extremidade v2 Graph para este exchange.
2. Se a troca falhar, AAD retornará uma exceção de concessão inválida. Geralmente, há uma das duas mensagens de erro `invalid_grant` ou `interaction_required` .
3. Quando a troca falhar, você deve solicitar consentimento. Mostrar alguma interface do usuário (UI) solicitando que o usuário conceda outro consentimento. Essa interface do usuário deve incluir um botão que aciona uma caixa de diálogo AAD consentimento usando nossa [API AAD autenticação.](~/concepts/authentication/auth-silent-aad.md)
4. Ao solicitar mais consentimento do AAD, você deve incluir no parâmetro `prompt=consent` [query-string-para](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) AAD, caso contrário, AAD não solicitará os outros escopos.
    * Em vez de `?scope={scopes}`
    * Use isso `?prompt=consent&scope={scopes}`
    * Verifique se isso inclui todos os escopos que você está solicitando ao usuário, por `{scopes}` exemplo, Mail.Read ou User.Read.
5. Depois que o usuário tiver concedido mais permissão, repetir o on-behalf-of-flow para obter acesso a essas outras APIs.

### <a name="non-aad-authentication"></a>Autenticação AAD não-autenticação

A solução de autenticação acima descrita só funciona para aplicativos e serviços que suportam AAD como um provedor de identidade. Os aplicativos que querem autenticar usando serviços não baseados em AAD devem continuar usando o fluxo de autenticação da Web baseado em [pop-up.](~/concepts/authentication.md)

> [!NOTE]
> O SSO é suportado para aplicativos de propriedade do cliente nos locatários AAD B2C.
