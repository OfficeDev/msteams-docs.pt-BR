---
title: Usar provedores OAuth externos
description: Descreve a autenticação usando provedores OAuth externo
ms.topic: how-to
ms.localizationpriority: high
keywords: Autenticação no Teams usando um provedor OAuth externo
ms.openlocfilehash: df9a9e36ecd203cd2b6c482af00b60ddfb145114
ms.sourcegitcommit: ca902f505a125641c379a917ee745ab418bd1ce6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2022
ms.locfileid: "63464256"
---
# <a name="use-external-oauth-providers"></a>Usar provedores OAuth externos

Você pode oferecer suporte a provedores OAuth externos ou de terceiros (3P), como o Google, GitHub, LinkedIn e Facebook usando a API `authenticate()` atualizada:

```JavaScript
function authenticate(authenticateParameters?: AuthenticateParameters)
``` 

Os itens a seguir são adicionados à API `authenticate()` para oferecer suporte a provedores OAuth externos:

* Parâmetro `isExternal`
* Dois valores de espaço reservado no parâmetro `url` existente

A tabela a seguir fornece a lista parâmetros e funções da API `authenticate()` juntamente com suas descrições:

| Parâmetro| Descrição|
| --- | --- |
|`isExternal` | O tipo de parâmetro é Booliano, que indica que a janela de autenticação é aberta em um navegador externo.|
|`failureCallback`| A função é chamada se a autenticação falhar e o pop-up de autenticação especificar o motivo da falha.|
|`height` |A altura preferencial para o pop-up. O valor pode ser ignorado se estiver fora dos limites aceitáveis.|
|`successCallback`| A função é chamada se a autenticação for bem-sucedida, com o resultado retornado do pop-up de autenticação. O código de autenticação é o resultado.|
|`url`  <br>|A URL do servidor de aplicativos 3P para o pop-up de autenticação, com os dois espaços reservados de parâmetro a seguir:</br> <br> - `oauthRedirectMethod`: passe o espaço reservado no `{}`. A plataforma do Teams substitui esse espaço reservado por um deeplink ou página da Web que informa ao servidor de aplicativos se a chamada é de uma plataforma móvel.</br> <br> - `authId`: Esse espaço reservado é substituído por UUID. O servidor de aplicativos o usa para manter a sessão.| 
|`width`|A largura preferencial para o pop-up. O valor pode ser ignorado se estiver fora dos limites aceitáveis.|

Para obter mais informações sobre parâmetros, confira [interface de parâmetros de autenticação](/javascript/api/@microsoft/teams-js/microsoftteams.authentication.authenticateparameters?view=msteams-client-js-latest&preserve-view=true).

## <a name="add-authentication-to-external-browsers"></a>Adicionar autenticação a navegadores externos

> [!NOTE]
> * No momento, você pode adicionar autenticação a navegadores externos somente para guias em dispositivos móveis. 
> * Use a versão beta do SDK do JS para aproveitar a funcionalidade. As versões beta estão disponíveis por meio do [NPM](https://www.npmjs.com/package/@microsoft/teams-js/v/1.12.0-beta.2).

A imagem a seguir fornece o fluxo para adicionar autenticação a navegadores externos:

 :::image type="content" source="../../../assets/images/tabs/tabs-authenticate-OAuth.PNG" alt-text="authenticate-OAuth" border="true":::

**Para adicionar autenticação a navegadores externos**

1. Inicie o processo de entrada de autenticação externo.

   O aplicativo 3P chama a função SDK `microsoftTeams.authentication.authenticate` com `isExternal` definido como verdadeiro para iniciar o processo de logon de autenticação externo. 

   O `url` aprovado contém espaços reservados para a `{authId}` e o`{oauthRedirectMethod}`.  


    ```JavaScript
    microsoftTeams.authentication.authenticate({
       url: 'https://3p.app.server/auth?oauthRedirectMethod={oauthRedirectMethod}&authId={authId}',
       isExternal: true,
       successCallback: function (result) {
       //sucess 
       } failureCallback: function (reason) {
       //failure 
        }
    });
    ```

2. O link do Teams é aberto em um navegador externo.

   Os clientes do Teams abrem a URL em um navegador externo depois de substituir os espaços reservados para `oauthRedirectMethod` e `authId` por valores adequados. 

   #### <a name="example"></a>Exemplo

   ```http
    https://3p.app.server/auth?oauthRedirectMethod=deeplink&authId=1234567890 
   ```

3. O servidor de aplicativos 3P responde.

   O servidor de aplicativos 3P recebe e salva a `url` com os dois parâmetros de consulta a seguir:

   | Parâmetro | Descrição|
   | --- | --- |
   | `oauthRedirectMethod` |Indica como o aplicativo 3P deve enviar a resposta da solicitação de autenticação de volta ao Teams, com um dos dois valores: deeplink ou página.|
   |`authId` | A ID de solicitação criada pelo Teams para essa solicitação de autenticação específica que precisa ser enviada de volta ao Teams por meio do deeplink.|

    > [!TIP]
    > O aplicativo 3P pode empacotar `authId`, `oauthRedirectMethod` no parâmetro de consulta OAuth `state` ao gerar a URL de logon para o OAuthProvider. O `state` contém a `authId` e o `oauthRedirectMethod` aprovados, quando o OAuthProvider redireciona de volta para o servidor 3P e o aplicativo 3P usa os valores para enviar a resposta de autenticação de volta ao Teams, conforme descrito em **6. A resposta do servidor de aplicativos 3P ao Teams**. 

4. O servidor de aplicativo 3P redireciona para o `url` especificado.

   O servidor de aplicativos 3P redireciona para a página de autenticação dos provedores OAuth no navegador externo. O `redirect_uri` é uma rota dedicada no servidor de aplicativos 3P. Você pode registrar a `redirect_uri` no console de desenvolvimento do provedor OAuth como estático, os parâmetros precisam ser enviados por meio do objeto de estado. 

   #### <a name="example"></a>Exemplo

    ```http
    https://accounts.google.com/o/oauth2/v2/auth?redirect_uri=https://3p.app.server/authredirect&state={"authId":"…","oauthRedirectMethod":"…"}&client_id=…    &response_type=code&access_type=offline&scope= … 
    ```

5. Entre no navegador externo.

   O usuário entra no navegador externo. Os provedores OAuth redirecionam de volta para o `redirect_uri` com o código de autenticação e o objeto de estado.

6. O servidor de aplicativos 3P verifica e responde ao Teams.

   O servidor de aplicativos 3P manipula a resposta e verifica o `oauthRedirectMethod`, que é retornado do provedor OAuth externo no objeto de estado para determinar se a resposta precisa ser retornada por meio do deeplink de retorno de chamada de autenticação ou por meio da página da Web que chama a `notifySuccess()`.

      ```JavaScript
      const state = JSON.parse(req.query.state)
      if (state.oauthRedirectMethod === 'deeplink') {
         return res.redirect('msteams://teams.microsoft.com/l/auth-callback?authId=${state.authId}&code=${req.query.code}')
      }
      else {
      // continue redirecting to a web-page that will call notifySuccsss() – usually this method is used in Teams-Web
      …
      ```

7. O aplicativo 3P gera um deeplink.

   O aplicativo 3P gera um deeplink para o Teams para dispositivo móvel no formato a seguir e envia o código de autenticação com a ID da sessão de volta ao Teams.

   ```JavaScript
   return res.redirect(`msteams://teams.microsoft.com/l/auth-callback?authId=${state.authId}&code=${req.query.code}`)
   ```

 8. O Teams chama o retorno de chamada de sucesso e envia o resultado.

    O Teams chama o retorno de chamada bem-sucedido e envia o resultado (código de autenticação) para o aplicativo 3P. O aplicativo 3P recebe o código no retorno de chamada bem-sucedido e usa o código para recuperar o token, depois as informações do usuário e atualiza a interface do usuário.

      ```JavaScript
      successCallback: function (result) { 
      … 
      } 
      ```

## <a name="see-also"></a>Confira também

* [Configurar provedores de identidade](../../../concepts/authentication/configure-identity-provider.md)
* [Fluxo de autenticação do Microsoft Teams para guias](auth-flow-tab.md)
