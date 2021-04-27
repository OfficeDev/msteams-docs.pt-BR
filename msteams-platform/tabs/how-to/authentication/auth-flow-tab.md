---
title: Fluxo de autenticação para guias
description: Descreve o fluxo de autenticação em guias
ms.topic: conceptual
localization_priority: Normal
keywords: guias de fluxo de autenticação do teams
ms.openlocfilehash: 012e38b0fa689527999237ccc07b7352fc00ae71
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020391"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Fluxo de autenticação do Microsoft Teams para guias

> [!NOTE]
> Para que a autenticação funcione para sua guia em clientes móveis, você deve garantir que você está usando pelo menos a versão 1.4.1 do SDK JavaScript do Microsoft Teams.
> O SDK do Teams inicia uma janela separada para fluxo de autenticação. De definir `SameSite` o atributo como **Lax**. O cliente da área de trabalho do Teams ou versões mais antigas do Chrome ou Safari não `SameSite` suportam =None.

OAuth 2.0 é um padrão aberto para autenticação e autorização usada pelo Azure Active Directory (AAD) e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams. Para obter mais informações, consulte [OAuth 2 simplificado](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é diferente porque as guias são semelhantes aos sites para que possam usar o OAuth 2.0 diretamente. Os bots fazem algumas coisas de forma diferente, mas os conceitos principais são idênticos.

Para um exemplo de fluxo de autenticação para guias e bots usando Node e o tipo de concessão implícita [OAuth 2.0,](https://oauth.net/2/grant-types/implicit/)consulte iniciar o fluxo de autenticação [para guias](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow).

> [!NOTE]
> Antes de mostrar um **botão de Logon** para o usuário e chamar a API em resposta à seleção do botão, você deve aguardar a conclusão da `microsoftTeams.authentication.authenticate` inicialização do SDK. Você pode passar um retorno de chamada para a API que é chamada quando a `microsoftTeams.initialize` inicialização é concluída.

![Diagrama de sequência de autenticação de tabulação](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. O usuário interage com o conteúdo na configuração da guia ou na página de conteúdo, normalmente um botão Entrar **ou** **Entrar.**
2. A guia constrói a URL para sua página inicial de autenticação. Opcionalmente, ele usa informações de placeholders de URL ou chama o método SDK do cliente do Teams para simplificar a experiência de autenticação `microsoftTeams.getContext()` para o usuário. Por exemplo, ao autenticar com o AAD, se o parâmetro estiver definido para o endereço de email do usuário, o usuário não precisa entrar se tiver feito `login_hint` isso recentemente. Isso porque o AAD usa as credenciais armazenadas em cache do usuário. A janela pop-up é mostrada brevemente e desaparece.
3. Em seguida, a guia chama o `microsoftTeams.authentication.authenticate()` geral e registra as `successCallback` e `failureCallback` funções.
4. O Teams abre a página inicial em um iframe em uma janela pop-up. A página inicial gera dados aleatórios, salva-os para validação futura e redireciona para o ponto de extremidade do provedor de identidade, como para o `state` `/authorize` `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` Azure AD. Substitua `<tenant id>` por sua própria id de locatário que seja context.tid.
Semelhante a outros fluxos de auth de aplicativos no Teams, a página inicial deve estar em um domínio que está em sua lista e no mesmo domínio que a página de redirecionamento de entrada `validDomains` de postagem.

    > [!NOTE]
    > O fluxo implícito de concessão do OAuth 2.0 chama um parâmetro na solicitação de autenticação, que contém dados de sessão exclusivos para impedir um ataque de falsificação de solicitação entre `state` [sites.](https://en.wikipedia.org/wiki/Cross-site_request_forgery) Os exemplos usam um GUID gerado aleatoriamente para os `state` dados.

5. No site do provedor, o usuário faz o acesso e concede acesso à guia.
6. O provedor leva o usuário para a página de redirecionamento OAuth 2.0 da guia com um token de acesso.
7. A guia verifica se o valor retornado corresponde ao que foi salvo anteriormente e chama , que, por sua vez, chama a `state` função registrada na etapa `microsoftTeams.authentication.notifySuccess()` `successCallback` 3.
8. O Teams fecha a janela pop-up.
9. A guia exibe a interface do usuário de configuração, atualiza ou recarrega o conteúdo das guias, dependendo de onde o usuário começou.

## <a name="treat-tab-context-as-hints"></a>Tratar o contexto da guia como dicas

Embora o contexto da guia fornece informações úteis sobre o usuário, não use essas informações para autenticar o usuário. Faça a autenticação do usuário mesmo que você receba as informações como parâmetros de URL para a URL de conteúdo da guia ou chamando a função no SDK do cliente do `microsoftTeams.getContext()` Microsoft Teams. Um ator mal-intencionado pode invocar sua URL de conteúdo de tabulação com seus próprios parâmetros. O ator também pode invocar uma página da Web que representa o Microsoft Teams para carregar sua URL de conteúdo de tabulação em um iframe e retornar seus próprios dados para a `getContext()` função. Você deve tratar as informações relacionadas à identidade no contexto da guia simplesmente como dicas e validá-las antes de usá-las. Consulte as anotações em [navegar até a página de autorização da página pop-up](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page).

## <a name="code-sample"></a>Exemplo de código

Código de exemplo mostrando o processo de autenticação de tabulação.

| **Exemplo de nome** | **Descrição** | **C#** | **Node.js** |
|-----------------|-----------------|-------------|------------|
| Autenticação de tabulação do Teams | Processo de autenticação para guias usando a AAD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/nodejs) |

## <a name="more-details"></a>Mais detalhes

Para uma implementação detalhada para autenticação de tabulação usando o AAD, consulte:

* [Autenticar um usuário em uma guia do Teams](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md)
