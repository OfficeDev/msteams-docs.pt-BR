---
title: Habilitar a autenticação usando o provedor OAuth de terceiros
description: Neste artigo, aprenda sobre o fluxo de autenticação em guias do Teams, o provedor OAuth de terceiros, o OAuth por Azure AD e exemplos de código de autenticação.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: 2edd52d80428e47a8586ec27de4b1595d872df8c
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144247"
---
# <a name="enable-authentication-using-third-party-oauth-provider"></a>Habilitar a autenticação usando o provedor OAuth de terceiros

Você pode habilitar a autenticação em seu aplicativo de guia usando provedores de identidade OAuth (IdP) de terceiros. Neste método, a identidade do usuário do aplicativo é validada e o acesso concedido por um OAuth IdP, tal como o Azure AD, Google, Facebook, GitHub ou qualquer outro provedor. Você precisará configurar uma relação de confiança com o IdP, e os usuários do seu aplicativo também devem ser registrados com ele.

> [!NOTE]
> Para que a autenticação funcione para sua guia em clientes móveis, você precisa garantir que está usando pelo menos a versão 1.4.1 do SDK de JavaScript do Microsoft Teams.  
> O SDK do Teams inicia uma janela separada para o fluxo de autenticação. Defina o atributo `SameSite` como **Lax**. O cliente de desktop do Teams ou versões anteriores do Chrome ou Safari não são compatíveis com `SameSite`=Nenhum.

## <a name="use-oauth-idp-to-enable-authentication"></a>Usar o OAuth IdP para habilitar a autenticação

O OAuth 2.0 é um padrão aberto de autenticação e autorização usado pelo Microsoft Azure Active Directory (Azure AD) e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams. Para obter mais informações, consulte [OAuth 2 simplificado](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é diferente porque as guias são semelhantes aos sites para que possam usar o OAuth 2.0diretamente. Os bots fazem algumas coisas de maneira diferente, mas os conceitos principais são idênticos.

Por exemplo, o fluxo de autenticação para guias e bots usando Node e o [tipo de concessão implícita OAuth 2.0](https://oauth.net/2/grant-types/implicit/), consulte [iniciar fluxo de autenticação para guias](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow).

Esta seção usa o Azure AD como um exemplo de um provedor de OAuth de terceiros para habilitar a autenticação em um aplicativo de guia.

> [!NOTE]
> Antes de mostrar um botão **Login** para o usuário e chamar a API `microsoftTeams.authentication.authenticate` em resposta à seleção do botão, você deve aguardar a conclusão da inicialização do SDK. Você pode passar um retorno de chamada para a API `microsoftTeams.initialize` que é chamada quando a inicialização é concluída.

![Diagrama de sequência de autenticação de tabulação](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. O usuário interage com o conteúdo na configuração da guia ou na página de conteúdo, geralmente um botão **Entrar** ou **Fazer login**.
2. A guia constrói o URL para sua página inicial de autenticação. Opcionalmente, ele usa informações de marcadores de URL ou chama o método `microsoftTeams.getContext()` do SDK do cliente do Teams para simplificar a experiência de autenticação para o usuário. Por exemplo, ao autenticar com um Azure AD, se o `login_hint` parâmetro estiver definido para o endereço de email do usuário, o usuário não precisa fazer logon se o fez recentemente. Isso ocorre porque o Azure Active Directory usa as credenciais em cache do usuário. A janela pop-up é mostrada brevemente e depois desaparece.
3. Em seguida, a guia chama o `microsoftTeams.authentication.authenticate()` geral e registra as `successCallback` e `failureCallback` funções.
4. O Teams abre a página inicial em um iframe em uma janela pop-up. A página inicial gera dados `state` aleatórios, salva-os para validação futura e redireciona para o ponto de extremidade `/authorize` do provedor de identidade, como `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` para Azure Active Directory. Substitua `<tenant id>` pelo seu próprio ID de locatário que é context.tid.
Semelhante a outros fluxos de autenticação de aplicativo no Teams, a página inicial deve estar em um domínio que esteja em sua lista `validDomains` e no mesmo domínio que a página de redirecionamento de entrada de postagem.

    > [!NOTE]
    > O fluxo de concessão implícita do OAuth 2.0 chama um parâmetro `state` na solicitação de autenticação, que contém dados de sessão exclusivos para evitar um [ataque de solicitação intersite forjada](https://en.wikipedia.org/wiki/Cross-site_request_forgery). Os exemplos usam um GUID gerado aleatoriamente para os dados `state`.

5. No site do provedor, o usuário entra e concede acesso à guia.
6. O provedor leva o usuário para a página de redirecionamento OAuth 2.0 da guia com um token de acesso.
7. A guia verifica se o valor `state` retornado corresponde ao que foi salvo anteriormente e chama `microsoftTeams.authentication.notifySuccess()`, que por sua vez chama a função `successCallback` registrada na etapa 3.
8. O Teams fecha a janela pop-up.
9. A guia exibe a interface do usuário de configuração, atualiza ou recarrega o conteúdo das guias, dependendo de onde o usuário iniciou.

> [!NOTE]
> Se o aplicativo for compatível com SAML SSO, o token JWT gerado por SSO da guia não poderá ser usado, pois não é compatível.

## <a name="treat-tab-context-as-hints"></a>Tratar o contexto da guia como dicas

Embora o contexto da guia forneça informações úteis sobre o usuário, não use estas informações para autenticar o usuário. Autentique o usuário mesmo se você obtiver as informações como parâmetros de URL para a URL de conteúdo da guia ou chamando a função `microsoftTeams.getContext()` no SDK do cliente do Microsoft Teams. Um ator mal-intencionado pode invocar a URL de conteúdo da guia com seus próprios parâmetros. O ator também pode invocar uma página da Web representando o Microsoft Teams para carregar a URL de conteúdo da guia em um iframe e retornar seus próprios dados para a função `getContext()`. Você deve tratar as informações relacionadas à identidade no contexto da guia como uma dica e validá-las antes de usar. Consulte as notas em [navegar até a página de autorização na sua página pop-up](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page).

## <a name="code-sample"></a>Exemplo de código

Código de exemplo mostrando o processo de autenticação da guia:

| **Nome de exemplo** | **Descrição** | **C#** | **Node.js** |
|-----------------|-----------------|-------------|------------|
| Autenticação de guia do Teams | Processo de autenticação para guias usando o Azure Active Directory. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/nodejs) |

## <a name="see-also"></a>Confira também

Para obter uma implementação detalhada para autenticação de tabulação usando o Azure Active Directory, consulte:

* [Autenticar um usuário em uma guia do Teams](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md)
