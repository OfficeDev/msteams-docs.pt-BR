---
title: Fluxo de autenticação para guias
description: Descreve o fluxo de autenticação em guias
ms.topic: conceptual
localization_priority: Normal
keywords: guias de fluxo de autenticação de equipes
ms.openlocfilehash: 1282c149beba0ff5b424585f566a703f48234fa2
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566688"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>fluxo de autenticação Microsoft Teams para guias

> [!NOTE]
> Para que a autenticação funcione para sua guia em clientes móveis, você deve garantir que você esteja usando pelo menos a versão 1.4.1 do Microsoft Teams JavaScript SDK.
> Teams O SDK lança janela separada para fluxo de autenticação. Defina o `SameSite` atributo para **Lax**. Teams cliente de desktop ou versões mais antigas do Chrome ou Safari não `SameSite` suportam =Nenhum.

OAuth 2.0 é um padrão aberto para autenticação e autorização usado por Azure Active Directory (AAD) e muitos outros provedores de identidade. Um entendimento básico do OAuth 2.0 é um pré-requisito para trabalhar com autenticação em Teams. Para obter mais informações, consulte [OAuth 2 simplificado](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal.](https://oauth.net/2/) O fluxo de autenticação para guias e bots é diferente porque as guias são semelhantes aos sites para que possam usar o OAuth 2.0 diretamente. Bots fazem algumas coisas de forma diferente, mas os conceitos principais são idênticos.

Para um exemplo de fluxo de autenticação para guias e bots usando o Nó e o [tipo de subvenção implícita OAuth 2.0,](https://oauth.net/2/grant-types/implicit/)consulte [iniciar o fluxo de autenticação para guias](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow).

> [!NOTE]
> Antes de mostrar um botão **de login** para o usuário e chamar a `microsoftTeams.authentication.authenticate` API em resposta à seleção do botão, você deve aguardar a inicialização do SDK para ser concluída. Você pode passar um retorno de chamada para a `microsoftTeams.initialize` API que é chamada quando a inicialização é concluída.

![Diagrama da sequência de autenticação da guia](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. O usuário interage com o conteúdo na configuração da guia ou na página de conteúdo, comumente um botão **De entrada** ou **login.**
2. A guia constrói a URL para sua página inicial auth. Opcionalmente, ele usa informações de espaços reservados de URL ou chamadas `microsoftTeams.getContext()` Teams método SDK do cliente para agilizar a experiência de autenticação para o usuário. Por exemplo, ao autenticar com AAD, se o `login_hint` parâmetro estiver definido no endereço de e-mail do usuário, o usuário não precisa fazer login se o fez recentemente. Isso ocorre porque o AAD usa as credenciais em cache do usuário. A janela pop-up é mostrada brevemente e depois desaparece.
3. Em seguida, a guia chama o `microsoftTeams.authentication.authenticate()` geral e registra as `successCallback` e `failureCallback` funções.
4. Teams abre a página inicial em um iframe em uma janela pop-up. A página inicial gera `state` dados aleatórios, salva-os para validação futura e redireciona para o ponto final do provedor de `/authorize` identidade, como para O `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` Azure AD. Substitua `<tenant id>` com seu próprio id inquilino que é context.tid.
Semelhante a outros fluxos de auth de aplicativo em Teams, a página inicial deve estar em um domínio que está em sua `validDomains` lista e no mesmo domínio que o sinal de postagem na página de redirecionamento.

    > [!NOTE]
    > O fluxo de subvenção implícita OAuth 2.0 exige um `state` parâmetro na solicitação de autenticação, que contém dados de sessão exclusivos para evitar um ataque de [falsificação de solicitação entre sites](https://en.wikipedia.org/wiki/Cross-site_request_forgery). Os exemplos usam um GUID gerado aleatoriamente para os `state` dados.

5. No site do provedor, o usuário faz a assinatura e concede acesso à guia.
6. O provedor leva o usuário para a página de redirecionamento OAuth 2.0 da guia com um token de acesso.
7. A guia verifica se o valor devolvido `state` corresponde ao que foi salvo anteriormente, e chama , que por sua vez chama a função registrada na etapa `microsoftTeams.authentication.notifySuccess()` `successCallback` 3.
8. Teams fecha a janela pop-up.
9. A guia exibe interface do usuário de configuração, atualiza ou recarrega o conteúdo das guias, dependendo de onde o usuário começou.

## <a name="treat-tab-context-as-hints"></a>Tratar o contexto da guia como dicas

Embora o contexto da guia forneça informações úteis sobre o usuário, não use essas informações para autenticar o usuário. Autenticar o usuário mesmo que você obtenha as informações como parâmetros de URL para a URL de conteúdo da guia ou chamando a `microsoftTeams.getContext()` função no Microsoft Teams SDK cliente. Um ator mal-intencionado pode invocar sua URL de conteúdo de guia com seus próprios parâmetros. O ator também pode invocar uma página da Web personificando Microsoft Teams para carregar sua URL de conteúdo de guia em um iframe e retornar seus próprios dados para a `getContext()` função. Você deve tratar as informações relacionadas à identidade no contexto da guia simplesmente como dicas e validá-las antes do uso. Consulte as notas em [navegação para a página de autorização da sua página pop-up](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page).

## <a name="code-sample"></a>Exemplo de código

Código de amostra mostrando o processo de autenticação de guias:

| **Nome da amostra** | **Descrição** | **C#** | **Node.js** |
|-----------------|-----------------|-------------|------------|
| Teams autenticação da guia Teams | Processo de autenticação para guias usando AAD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/nodejs) |

## <a name="more-details"></a>Mais detalhes

Para obter uma implementação detalhada para autenticação de guias usando AAD, consulte:

* [Autenticar um usuário em uma guia Teams](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md)
