---
title: Fluxo de autenticação para guias
description: Descreve o fluxo de autenticação em guias
ms.topic: conceptual
keywords: guias de fluxo de autenticação do Teams
ms.openlocfilehash: 9505419a6594529bcf8d19a90d029705e573c67b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014583"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Fluxo de autenticação do Microsoft Teams para guias

> [!Note]
> Para que a autenticação funcione para sua guia em clientes móveis, você precisa garantir que esteja usando pelo menos a versão 1.4.1 do SDK JavaScript do Teams.
> O SDK do Teams inicia uma janela separada para o fluxo de autenticação e, portanto, o atributo samesite pode ser definido como 'Mila'. Atualmente, SameSite=None não é compatível com o cliente de área de trabalho do Teams ou versões mais antigas do Chrome ou Safari.

O OAuth 2.0 é um padrão aberto para autenticação e autorização usados pelo Azure AD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams; [Aqui está uma boa visão geral](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal.](https://oauth.net/2/) O fluxo de autenticação para guias e bots é um pouco diferente porque as guias são muito semelhantes aos sites para que possam usar o OAuth 2.0 diretamente; os bots não são e devem fazer algumas coisas diferentes, mas os principais conceitos são idênticos.

*See*, [Initiate authentication flow for tabs](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow) for an example of authentication flow for tabs and bots using Node and the [OAuth 2.0 implicit grant type](https://oauth.net/2/grant-types/implicit/).

![Diagrama de sequência de autenticação por tabulação](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. O usuário interage com o conteúdo na configuração da guia ou na página de conteúdo, geralmente um botão rotulado como "Entrar" ou "Entrar".
2. A guia constrói a URL para sua página inicial de autenticação, opcionalmente usando informações de espaço reservados de URL ou chamando o método SDK do cliente do Teams para simplificar a experiência de autenticação para o `microsoftTeams.getContext()` usuário. Por exemplo, ao autenticar com o Azure AD, se o parâmetro for definido para o endereço de email do usuário, o usuário poderá não ter que entrar se tiver feito isso recentemente, porque o Azure AD usará as credenciais armazenadas em cache do usuário, se possível: o pop-up piscará brevemente e `login_hint` desaparecerá.
3. Em seguida, a guia chama `microsoftTeams.authentication.authenticate()` o método e registra as funções e as `successCallback` `failureCallback` funções.
4. O Teams abre a página inicial em um iframe em uma janela pop-up. A página inicial gera dados aleatórios, salva-os para validação futura e redireciona para o ponto de extremidade do provedor de identidade, como para o `state` `/authorize` `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` Azure AD. Substitua `<tenant id>` pela sua própria ID de locatário (context.tid).
    * Como outros fluxos de auth de aplicativos no Teams, a página inicial deve estar em um domínio que está em sua lista e no mesmo domínio que a página de redirecionamento `validDomains` pós-logon.
    * **IMPORTANTE:** as chamadas implícitas de fluxo de concessão do OAuth 2.0 para um parâmetro na solicitação de autenticação que contém dados de sessão exclusivos para evitar um ataque de solicitação de falsificação entre `state` [sites.](https://en.wikipedia.org/wiki/Cross-site_request_forgery) Os exemplos a seguir usam um GUID gerado aleatoriamente para os `state` dados.
5. No site do provedor, o usuário faz o acesso e concede acesso à guia.
6. O provedor leva o usuário para a página de redirecionamento OAuth 2.0 da guia com um token de acesso.
7. A guia verifica se o valor retornado corresponde ao que foi salvo anteriormente e chama, o que, por sua vez, chama a `state` função registrada na etapa `microsoftTeams.authentication.notifySuccess()` `successCallback` 3.
8. O Teams fecha a janela pop-up.
9. A guia exibe a interface do usuário de configuração ou atualiza ou recarrega o conteúdo das guias, dependendo de onde o usuário começou.

## <a name="treat-tab-context-as-hints"></a>Tratar o contexto da guia como dicas

Embora o contexto da guia fornece informações úteis sobre o usuário, não use essas informações para autenticar o usuário, independentemente de você usá-lo como parâmetros de URL para a URL de conteúdo da guia ou chamando a função no SDK do cliente `microsoftTeams.getContext()` do Microsoft Teams. Um ator mal-intencionado pode invocar a URL do conteúdo da guia com seus próprios parâmetros, e uma página da Web que representa o Microsoft Teams pode carregar a URL do conteúdo da guia em um iframe e retornar seus próprios dados para a `getContext()` função. Você deve tratar as informações relacionadas à identidade no contexto de guia simplesmente como dicas e validá-las antes de usá-las. Consulte as anotações em [Navegar para a página de autorização na sua página pop-up.](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page)

## <a name="samples"></a>Exemplos

Para ver o código de exemplo mostrando o processo de autenticação de guia, confira:

* [Exemplo de autenticação de guia do Microsoft Teams (Nó)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Exemplo de autenticação de guia do Microsoft Teams (C#)](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="more-details"></a>Mais detalhes

Para ver um passo a passo de implementação detalhado para autenticação de guia voltada para o Azure Active Directory, confira:

* [Autenticar um usuário em uma guia do Microsoft Teams](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md)
