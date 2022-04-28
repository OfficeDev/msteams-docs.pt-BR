---
title: Atributo de cookie SameSite
author: laujan
description: Saiba mais sobre tipos de cookies, incluindo cookies SameSite, seus atributos, suas implicações em guias do Teams, módulos de tarefa e extensões de mensagem e sua autenticação no Teams
keywords: atributos de cookie samesite
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: 1fbaf46da93a0d7c253f1f5d2ad6c9ae1764565a
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104487"
---
# <a name="samesite-cookie-attribute"></a>Atributo de cookie SameSite

Cookies são cadeias de caracteres de texto enviadas de sites e armazenadas em um computador pelo navegador da Web. Eles são usados para autenticação e personalização. Por exemplo, os cookies são usados para recuperar informações com estado, preservar as configurações do usuário, registrar a atividade de navegação e exibir anúncios relevantes. Os cookies sempre são vinculados a um domínio específico e são instalados por várias partes.

## <a name="types-of-cookies"></a>Tipos de cookies

Os tipos de cookie e seus escopos correspondentes são os seguintes:

|Cookie|Escopo|
| ------ | ------ |
|Cookie de primeira parte|Um cookie de terceiros é criado por sites que um usuário visita. Ele é usado para salvar dados, como itens de carrinho de compras, credenciais de entrada. Por exemplo, cookies de autenticação e outras análises.|
|Cookie de terceiros|Um cookie de terceiros é tecnicamente o mesmo que um cookie de terceiros. A diferença é que os dados são compartilhados com terceiros por meio de um contrato de parceria de dados. Por exemplo, [Microsoft Teams análise e relatórios](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference). |
|Cookie de terceiros|Um cookie de terceiros é instalado por um domínio diferente do que o usuário visitou explicitamente e é usado principalmente para acompanhamento. Por exemplo, **botões Like** , serviço de anúncios e chats ao vivo.|

## <a name="cookies-and-http-requests"></a>Cookies e solicitações HTTP

Antes da introdução das restrições sameSite, os cookies eram armazenados no navegador. Eles foram anexados a cada solicitação http da Web e enviados ao servidor pelo `Set Cookie` cabeçalho de resposta HTTP. Esse método introduziu vulnerabilidades de segurança, como Solicitação Entre Sites Forjada, chamadas de ataques CSRF. O componente SameSite reduziu a exposição por meio de sua implementação e gerenciamento no cabeçalho SetCookie.

## <a name="samesite-cookie-attribute-initial-release"></a>Atributo de cookie SameSite: versão inicial

O Google Chrome versão 51 introduziu a `SetCookie SameSite` especificação como um atributo opcional. A partir do Build 17672, Windows 10 suporte a cookie SameSite para o [navegador MicrosoftEdge&nbsp;](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/).

Você pode recusar a adição do atributo de cookie `SetCookie` SameSite ao cabeçalho ou adicioná-lo com uma das duas configurações, **Lax** e **Strict**. Um atributo SameSite não implementado foi considerado o estado padrão.

## <a name="samesite-cookie-attribute-2020-release"></a>Atributo de cookie SameSite: versão 2020

O Chrome 80, lançado em fevereiro de 2020, apresenta novos valores de cookie e impõe políticas de cookie por padrão. Três valores são passados para o atributo SameSite atualizado: **Strict**, **Lax** ou **None**. Se não for especificado, o atributo SameSite de cookies levará o valor `SameSite=Lax` por padrão.

Os atributos de cookie SameSite são os seguintes:

|Setting | Execução | Valor |Especificação de atributo |
| -------- | ----------- | --------|--------|
| **Lax**  | Os cookies são enviados automaticamente somente em **um contexto de terceiros** e com solicitações HTTP GET. Os cookies SameSite são retidos em subconsultas entre sites, como chamadas para carregar imagens ou iframes. Eles são enviados quando um usuário navega para a URL de um site externo, por exemplo, seguindo um link.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Estrito** |O navegador envia apenas cookies para solicitações de contexto de terceiros. Essas são solicitações originadas do site que definem o cookie. Se a solicitação tiver sido originada de uma URL diferente da do local atual, nenhum dos cookies marcados com o `Strict` atributo será enviado.| Opcional |`Set-Cookie: key=value; SameSite=Strict`|
| **Nenhum** | Os cookies são enviados em solicitações de contexto de primeira parte e entre origens; no entanto, o valor deve ser **`None`** definido explicitamente como e todas as solicitações do navegador devem seguir o protocolo **HTTPS** **`Secure`** e incluir o atributo que requer uma conexão criptografada. Os cookies que não aderem a esse requisito são **rejeitados**. <br/>**Ambos os atributos são necessários juntos**. Se  **`None`** for especificado sem ou **`Secure`**  se o protocolo HTTPS não for usado, os cookies de terceiros serão rejeitados.| Opcional, mas, se definido, o protocolo HTTPS é necessário. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Teams implicações e ajustes

1. Habilite a configuração relevante do SameSite para seus cookies e valide se seus aplicativos e extensões continuam funcionando em Teams.
1. Se seus aplicativos ou extensões falharem, faça as correções necessárias antes da versão do Chrome 80.
1. Os parceiros internos da Microsoft podem ingressar na seguinte equipe para obter mais informações ou ajudar com esse problema: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47>.

> [!NOTE]
> Você deve definir atributos SameSite para refletir o uso pretendido para seus cookies. Não dependa do comportamento padrão do navegador. Para obter mais informações, consulte [Desenvolvedores: Prepare-se para o novo SameSite=None; Secure Cookie Configurações](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Guias, módulos de tarefa e extensões de mensagem

* Teams guias usadas para `<iframes>` inserir conteúdo que é exibido em um contexto de nível superior ou de primeira parte.
* Os módulos de tarefas permitem que você crie experiências pop-up modais em seu aplicativo Teams. Semelhante a uma guia, uma janela modal é aberta dentro da página atual.
* As extensões de mensagem permitem inserir conteúdo enriquecido em uma mensagem de chat de recursos externos.

Todos os cookies usados pelo conteúdo inserido são considerados como de terceiros quando o site é exibido em um `<iframe>`. Além disso, se todos os recursos remotos em uma página dependerem de cookies `<img>` `<script>` sendo enviados com uma solicitação e marcas, fontes externas e conteúdo personalizado, você deverá garantir que eles sejam marcados para uso entre sites, `SameSite=None; Secure` como ou garantir que um fallback esteja em vigor.

### <a name="authentication"></a>Autenticação

Você deve usar o fluxo de autenticação baseado na Web para o seguinte:

* Páginas de conteúdo inseridas em guias.
* Página de configuração, módulo de tarefa e extensão de mensagem.
* Bot de conversa com um módulo de tarefa.

De acordo com as restrições do SameSite atualizadas, um navegador não adicionará um cookie a um site já autenticado se o link derivar de um site externo. Você deve garantir que os cookies de autenticação estejam marcados para uso entre sites `SameSite=None; Secure` ou garantir que um fallback esteja em vigor.

## <a name="android-system-webview"></a>WebView do Sistema Android

O Android WebView é um componente do sistema Chrome que permite que aplicativos Android exibam o conteúdo da Web. Embora as novas restrições sejam padrão, começando com o Chrome 80, elas não são impostas imediatamente em WebViews. Eles serão aplicados no futuro. Para se preparar, o Android permite que aplicativos nativos definam cookies diretamente por meio da [API cookieManager](https://developer.android.com/reference/android/webkit/CookieManager).

> [!NOTE]
>
> * Você deve declarar cookies de terceiros como `SameSite=Lax` ou `SameSite=Strict`, conforme apropriado.
> * Você deve declarar cookies de terceiros como `SameSite=None; Secure`.

## <a name="see-also"></a>Confira também

* [Exemplos de SameSite](https://github.com/GoogleChromeLabs/samesite-examples)
* [Receitas de cookie SameSite](https://web.dev/samesite-cookie-recipes/)
* [Clientes incompatíveis conhecidos]( https://www.chromium.org/updates/same-site/incompatible-clients)
* [Desenvolvedores: Prepare-se para o Novo SameSite=None; Configurações Seguras de Cookies](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)
* [Próximas Alterações de Cookies do SameSite no ASP.NET e ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
* [Cookies HTTP](https://developer.mozilla.org/docs/Web/HTTP/Cookies)
