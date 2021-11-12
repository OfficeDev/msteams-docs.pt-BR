---
title: Fluxo de autenticação para guias
description: Descreve o fluxo de autenticação em guias, OAuth por AAD e fornece exemplo de código
ms.topic: conceptual
ms.localizationpriority: medium
keywords: guias de fluxo de autenticação do teams
ms.openlocfilehash: 2d054ef841bf4f05be4e662d77b999c654670f45
ms.sourcegitcommit: 58fe8a87b988850ae6219c55062ac34cd8bdbf66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60949646"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Microsoft Teams fluxo de autenticação para guias

> [!NOTE]
> Para que a autenticação funcione para sua guia em clientes móveis, você precisa garantir que esteja usando pelo menos a versão 1.4.1 do SDK do Microsoft Teams JavaScript.  
> Teams SDK inicia janela separada para fluxo de autenticação. De definir `SameSite` o atributo como **Lax**. Teams cliente da área de trabalho ou versões mais antigas do Chrome ou Safari não `SameSite` suportam =None.

OAuth 2.0 é um padrão aberto para autenticação e autorização usada por Azure Active Directory (AAD) e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams. Para obter mais informações, consulte [OAuth 2 simplificado](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é diferente porque as guias são semelhantes aos sites para que possam usar o OAuth 2.0 diretamente. Os bots fazem algumas coisas de forma diferente, mas os conceitos principais são idênticos.

Por exemplo, o fluxo de autenticação para guias e bots usando Node e o tipo de concessão implícito [OAuth 2.0,](https://oauth.net/2/grant-types/implicit/)consulte iniciar o fluxo de autenticação [para guias](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow).

> [!NOTE]
> Antes de mostrar um **botão de Logon** para o usuário e chamar a API em resposta à seleção do botão, você deve aguardar a conclusão da `microsoftTeams.authentication.authenticate` inicialização do SDK. Você pode passar um retorno de chamada para a API que é chamada quando a `microsoftTeams.initialize` inicialização é concluída.

![Diagrama de sequência de autenticação de tabulação](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. O usuário interage com o conteúdo na configuração da guia ou na página de conteúdo, normalmente um botão Entrar **ou** **Entrar.**
2. A guia constrói a URL para sua página inicial de autenticação. Opcionalmente, ele usa informações de placeholders de URL ou chamadas Teams método SDK do cliente para simplificar a experiência de autenticação `microsoftTeams.getContext()` para o usuário. Por exemplo, ao autenticar com AAD, se o parâmetro estiver definido para o endereço de email do usuário, o usuário não precisa entrar se tiver feito isso `login_hint` recentemente. Isso porque AAD usa as credenciais armazenadas em cache do usuário. A janela pop-up é mostrada brevemente e desaparece.
3. Em seguida, a guia chama o `microsoftTeams.authentication.authenticate()` geral e registra as `successCallback` e `failureCallback` funções.
4. Teams abre a página inicial em um iframe em uma janela pop-up. A página inicial gera dados aleatórios, salva-os para validação futura e redireciona para o ponto de extremidade do provedor de identidade, como para o `state` `/authorize` `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` Azure AD. Substitua `<tenant id>` por sua própria id de locatário que seja context.tid.
Semelhante a outros fluxos de auth de aplicativos no Teams, a página inicial deve estar em um domínio que está em sua lista e no mesmo domínio que a página de redirecionamento de entrada de `validDomains` postagem.

    > [!NOTE]
    > O fluxo implícito de concessão do OAuth 2.0 chama um parâmetro na solicitação de autenticação, que contém dados de sessão exclusivos para impedir um ataque de falsificação de solicitação entre `state` [sites.](https://en.wikipedia.org/wiki/Cross-site_request_forgery) Os exemplos usam um GUID gerado aleatoriamente para os `state` dados.

5. No site do provedor, o usuário faz login e concede acesso à guia.
6. O provedor leva o usuário para a página de redirecionamento OAuth 2.0 da guia com um token de acesso.
7. A guia verifica se o valor retornado corresponde ao que foi salvo anteriormente e chama , que, por sua vez, chama a `state` função registrada na etapa `microsoftTeams.authentication.notifySuccess()` `successCallback` 3.
8. Teams fecha a janela pop-up.
9. A guia exibe a interface do usuário de configuração, atualiza ou recarrega o conteúdo das guias, dependendo de onde o usuário começou.

## <a name="treat-tab-context-as-hints"></a>Tratar o contexto da guia como dicas

Embora o contexto da guia fornece informações úteis sobre o usuário, não use essas informações para autenticar o usuário. Faça a autenticação do usuário mesmo que você receba as informações como parâmetros de URL para a URL de conteúdo da guia ou chamando a função no SDK do cliente Microsoft Teams `microsoftTeams.getContext()` cliente. Um ator mal-intencionado pode invocar sua URL de conteúdo de tabulação com seus próprios parâmetros. O ator também pode invocar uma página da Web que Microsoft Teams carregar sua URL de conteúdo de tabulação em um iframe e retornar seus próprios dados para a `getContext()` função. Você deve tratar as informações relacionadas à identidade no contexto da guia como uma dica e validá-la antes de usá-la. Consulte as anotações em [navegar até a página de autorização da página pop-up](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page).

## <a name="code-sample"></a>Exemplo de código

Código de exemplo mostrando o processo de autenticação de tabulação:

| **Nome do exemplo** | **Descrição** | **C#** | **Node.js** |
|-----------------|-----------------|-------------|------------|
| Teams autenticação de tabulação | Processo de autenticação para guias usando AAD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/nodejs) |

## <a name="see-also"></a>Confira também

Para uma implementação detalhada para autenticação de tabulação usando AAD, consulte:

* [Autenticar um usuário em uma Teams guia](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md)
