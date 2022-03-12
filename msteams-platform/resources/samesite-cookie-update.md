---
title: Atributo de cookie SameSite
author: laujan
description: Saiba mais sobre tipos de cookies, incluindo cookies SameSite, seus atributos, suas implicações em guias de Teams, módulos de tarefas e extensões de mensagens e sua autenticação no Teams
keywords: atributos de cookie samesite
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: 8a1d8cff46612091749ba6801f42c79a3d997c97
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63452582"
---
# <a name="samesite-cookie-attribute"></a>Atributo de cookie SameSite

Cookies são cadeias de caracteres de texto enviadas de sites e armazenadas em um computador pelo navegador da Web. Eles são usados para autenticação e personalização. Por exemplo, cookies são usados para lembrar informações de estado, preservar configurações do usuário, registrar atividades de navegação e exibir anúncios relevantes. Os cookies são sempre vinculados a um determinado domínio e são instalados por várias partes.

## <a name="types-of-cookies"></a>Tipos de cookies

Os tipos de cookie e seus escopos correspondentes são os seguinte:

|Cookie|Escopo|
| ------ | ------ |
|Cookie de primeira parte|Um cookie de primeira parte é criado por sites que um usuário visita. Ele é usado para salvar dados, como itens de carrinho de compras, entrar em credenciais. Por exemplo, cookies de autenticação e outras análises.|
|Cookie de terceiros|Um cookie de terceiros é tecnicamente o mesmo que um cookie de primeira parte. A diferença é que os dados são compartilhados com uma segunda parte por meio de um contrato de parceria de dados. Por exemplo, [Microsoft Teams análise e relatórios](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference). |
|Cookie de terceiros|Um cookie de terceiros é instalado por um domínio diferente do que o usuário visitou explicitamente e é usado principalmente para rastreamento. Por exemplo, **botões Like** , serviço de ad e chats ao vivo.|

## <a name="cookies-and-http-requests"></a>Cookies e solicitações HTTP

Antes da introdução das restrições do SameSite, os cookies eram armazenados no navegador. Eles foram anexados a cada solicitação da Web HTTP e enviados ao servidor pelo `Set Cookie` cabeçalho de resposta HTTP. Este método introduziu vulnerabilidades de segurança, como Falsificação de Solicitação de Site Cruzado, chamadas de ataques CSRF. O componente SameSite reduziu a exposição por meio de sua implementação e gerenciamento no header SetCookie.

## <a name="samesite-cookie-attribute-initial-release"></a>Atributo cookie SameSite: versão inicial

O Google Chrome versão 51 introduziu a `SetCookie SameSite` especificação como um atributo opcional. A partir do Build 17672, Windows 10 o suporte a cookies SameSite para o [navegador MicrosoftEdge&nbsp;](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/).

Você pode optar por não adicionar o atributo cookie `SetCookie` SameSite ao header ou adicioná-lo com uma das duas configurações, **Lax** e **Strict**. Um atributo SameSite não simplificado foi considerado o estado padrão.

## <a name="samesite-cookie-attribute-2020-release"></a>Atributo de cookie SameSite: versão 2020

O Chrome 80, lançado em fevereiro de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão. Três valores são passados para o atributo SameSite atualizado: **Strict**, **Lax** ou **None**. Se não for especificado, o atributo Cookies SameSite assume o valor `SameSite=Lax` por padrão.

Os atributos de cookie sameSite são os seguinte:

|Setting | Imposição | Valor |Especificação de Atributo |
| -------- | ----------- | --------|--------|
| **Lax**  | Os cookies são enviados automaticamente somente em **um contexto de primeira** parte e com solicitações GET HTTP. Os cookies sameSite são retidos em solicitações de subsite cruzados, como chamadas para carregar imagens ou iframes. Eles são enviados quando um usuário navega para a URL de um site externo, por exemplo, seguindo um link.| **Padrão** |`Set-Cookie: key=value; SameSite=Lax`|
| **Estrito** |O navegador envia apenas cookies para solicitações de contexto de primeira parte. São solicitações provenientes do site que definiram o cookie. Se a solicitação tiver sido originada de uma URL diferente da do local atual, nenhum dos cookies marcados com o `Strict` atributo será enviado.| Opcional |`Set-Cookie: key=value; SameSite=Strict`|
| **Nenhum** | Os cookies são enviados no contexto de primeira parte e em solicitações de origem cruzada; no entanto, o valor deve **`None`** ser definido explicitamente como e todas as solicitações de navegador devem seguir o **protocolo HTTPS** **`Secure`** e incluir o atributo que exige uma conexão criptografada. Os cookies que não aderem a esse requisito são **rejeitados**. <br/>**Ambos os atributos são necessários juntos**. Se  **`None`** for especificado sem ou **`Secure`**  se o protocolo HTTPS não for usado, os cookies de terceiros serão rejeitados.| Opcional, mas, se definido, o protocolo HTTPS é necessário. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Teams implicações e ajustes

1. Habilita a configuração relevante do SameSite para seus cookies e valide se seus aplicativos e extensões continuam a funcionar em Teams.
1. Se seus aplicativos ou extensões falharem, faça as correções necessárias antes da versão do Chrome 80.
1. Os parceiros internos da Microsoft podem ingressar na equipe a seguir para obter mais informações ou ajudar com este problema: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47>.

> [!NOTE]
> Você deve definir atributos SameSite para refletir o uso pretendido para seus cookies. Não confie no comportamento padrão do navegador. Para obter mais informações, consulte [Desenvolvedores: Prepare-se para New SameSite=None; Secure Cookie Configurações](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-messaging-extensions"></a>Guias, módulos de tarefas e extensões de mensagens

* Teams guias usam para `<iframes>` inserir conteúdo que é exibido em um contexto de nível superior ou de primeira parte.
* Os módulos de tarefas permitem que você crie experiências pop-up modais em seu aplicativo Teams. Semelhante a uma guia, uma janela modal é aberta dentro da página atual.
* Extensões de mensagens permitem inserir conteúdo enriquecido em uma mensagem de chat de recursos externos.

Todos os cookies usados pelo conteúdo incorporado são considerados como terceiros quando o site é exibido em um `<iframe>`. Além disso, se qualquer recurso remoto em uma página depender de cookies `<img>` `<script>` que estão sendo enviados com uma solicitação e marcas, fontes externas e conteúdo personalizado, você deve garantir que eles sejam marcados para uso entre sites, `SameSite=None; Secure` como ou garantir que um fallback está no local.

### <a name="authentication"></a>Autenticação

Você deve usar o fluxo de autenticação baseado na Web para o seguinte:

* Páginas de conteúdo incorporadas em guias.
* Página de configuração, módulo de tarefa e extensão de mensagens.
* Bot de conversa com um módulo de tarefa.

De acordo com as restrições atualizadas do SameSite, um navegador não adiciona um cookie a um site já autenticado se o link deriva de um site externo. Você deve garantir que seus cookies de autenticação sejam marcados para uso entre sites `SameSite=None; Secure` ou garantir que um fallback está no local.

## <a name="android-system-webview"></a>Android System WebView

O Android WebView é um componente do sistema Chrome que permite que aplicativos Android exibem o conteúdo da Web. Embora as novas restrições sejam padrão, começando com o Chrome 80, elas não são impostas imediatamente no WebViews. Eles serão aplicados no futuro. Para se preparar, o Android permite que aplicativos nativos de definir cookies diretamente por meio da [API CookieManager](https://developer.android.com/reference/android/webkit/CookieManager).

> [!NOTE]
>
> * Você deve declarar cookies de primeira parte como `SameSite=Lax` ou `SameSite=Strict`, conforme apropriado.
> * Você deve declarar cookies de terceiros como `SameSite=None; Secure`.

## <a name="see-also"></a>Confira também

* [Exemplos de SameSite](https://github.com/GoogleChromeLabs/samesite-examples)
* [Receitas de cookie sameSite](https://web.dev/samesite-cookie-recipes/)
* [Clientes incompatíveis conhecidos]( https://www.chromium.org/updates/same-site/incompatible-clients)
* [Desenvolvedores: Prepare-se para o Novo SameSite=None; Configurações Seguras de Cookies](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)
* [Próximas Alterações de Cookies do SameSite no ASP.NET e ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
* [Cookies HTTP](https://developer.mozilla.org/docs/Web/HTTP/Cookies)
