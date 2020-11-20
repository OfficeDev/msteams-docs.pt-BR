---
title: Fluxo de autenticação para guias
description: Descreve o fluxo de autenticação em guias
keywords: guias de fluxo de autenticação de equipes
ms.openlocfilehash: de5e0312e4523c3adef211dc03b0349c205f92cb
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346676"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Fluxo de autenticação do Microsoft Teams para guias

> [!Note]
> Para que a autenticação funcione para sua guia em clientes móveis, é necessário garantir que você esteja usando pelo menos a versão 1.4.1 do SDK do Microsoft Teams JavaScript.
> O Teams SDK inicia a janela separada para o fluxo de autenticação e, portanto, o atributo SameSite pode ser definido como ' LAX '. Atualmente, SameSite = nenhum não é suportado pelo cliente do teams desktop ou por versões mais antigas do Chrome ou do Safari.

O OAuth 2,0 é um padrão aberto para autenticação e autorização usados pelo Azure AD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Microsoft Teams; [Veja aqui uma boa visão geral](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é um pouco diferente porque guias são muito semelhantes aos sites para que eles possam usar o OAuth 2,0 diretamente; os bots não são e devem fazer algumas coisas de forma diferente, mas os conceitos principais são idênticos.

para obter um exemplo que demonstra o fluxo de autenticação para guias e bots usando o nó usando o [tipo de concessão implícita OAuth 2,0](https://oauth.net/2/grant-types/implicit/).

![Diagrama de sequência de autenticação de guia](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. O usuário interage com o conteúdo na configuração da guia ou página de conteúdo, normalmente um botão rotulado "entrar" ou "fazer logon".
2. A guia constrói a URL da sua página inicial de autenticação, usando, opcionalmente, as informações dos espaços reservados de URL ou chamando `microsoftTeams.getContext()` o método SDK do cliente do teams para simplificar a experiência de autenticação para o usuário. Por exemplo, ao autenticar com o Azure AD, se o `login_hint` parâmetro estiver definido como o endereço de email do usuário, o usuário pode não ter que fazer logon se tiver feito isso recentemente, porque o Azure ad usará as credenciais armazenadas em cache do usuário, se possível: o pop-up piscará brevemente e desaparecerá.
3. Em seguida, a guia chama o `microsoftTeams.authentication.authenticate()` método e registra as `successCallback` `failureCallback` funções e.
4. O Microsoft Teams abre a página inicial em um iframe em uma janela pop-up. A página inicial gera dados aleatórios `state` , salva-os para validação futura e redireciona para o ponto de extremidade do provedor de identidade, como `/authorize` para o `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` Azure AD. Substitua `<tenant id>` por sua própria ID de locatário (Context. tid).
    * Como outros fluxos de autenticação de aplicativos no Microsoft Teams, a página inicial deve estar em um domínio que está em sua `validDomains` lista e no mesmo domínio que a página de redirecionamento após o logon.
    * **Importante**: o fluxo de concessão implícita do OAuth 2,0 chama um `state` parâmetro na solicitação de autenticação que contém dados de sessão exclusivos para evitar um [ataque de falsificação de solicitação entre sites](https://en.wikipedia.org/wiki/Cross-site_request_forgery). Os exemplos abaixo usam um GUID gerado aleatoriamente para os `state` dados.
5. No site do provedor, o usuário entra e concede acesso à guia.
6. O provedor leva o usuário para a página de redirecionamento OAuth 2,0 da guia com um token de acesso.
7. A guia verifica se o `state` valor retornado corresponde ao que foi salvo anteriormente e, por `microsoftTeams.authentication.notifySuccess()` sua vez, chama a `successCallback` função registrada na etapa 3.
8. O Microsoft Teams fecha a janela pop-up.
9. A guia exibe a interface do usuário de configuração ou atualiza ou recarrega o conteúdo das guias, dependendo de onde o usuário iniciou.

## <a name="treat-tab-context-as-hints"></a>Tratar contexto da guia como dicas

Embora o contexto de tabulação forneça informações úteis sobre o usuário, não use essas informações para autenticar o usuário se você o recebe como parâmetros de URL para a URL de conteúdo da sua guia ou chamando a `microsoftTeams.getContext()` função no SDK do cliente do Microsoft Teams. Um ator mal-intencionado pode invocar a URL de conteúdo da guia com seus próprios parâmetros, e uma página da Web representando o Microsoft Teams pode carregar sua URL de conteúdo de tabulação em um iframe e retornar seus próprios dados para a `getContext()` função. Você deve tratar as informações relacionadas à identidade no contexto da guia simplesmente como dicas e validá-las antes de usar.

## <a name="samples"></a>Exemplos

Para ver o código de exemplo que mostra o processo de autenticação de guia, consulte:

* [Exemplo de autenticação de guia do Microsoft Teams (nó)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Exemplo de autenticação de guia do Microsoft Teams (C#)](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="more-details"></a>Mais detalhes

Para obter uma implementação detalhada passo a passo para a autenticação de guia direcionada ao Azure Active Directory, confira:

* [Autenticar um usuário em uma guia do Microsoft Teams](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md)
