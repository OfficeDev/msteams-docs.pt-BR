---
title: Atributo de cookie SameSite
author: laujan
description: Saiba mais sobre Tipos de cookies, incluindo cookies SameSite, seus atributos, suas implicações em guias do Teams, módulos de tarefas e extensões de mensagem e sua autenticação no Teams
keywords: atributos de cookie samesite
ms.topic: reference
ms.localizationpriority: high
ms.author: lomeybur
ms.openlocfilehash: 7bf6d5a986a2111ba624534aa13b0aaa2866120c
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65110334"
---
# <a name="samesite-cookie-attribute"></a>Atributo de cookie SameSite

Cookies são cadeias de caracteres de texto enviadas de sites e armazenadas em um computador pelo navegador. Eles são usados para autenticação e personalização. Por exemplo, os cookies são usados para recuperar informações com estado, preservar as configurações do usuário, registrar a atividade de navegação e exibir anúncios relevantes. Os cookies sempre são vinculados a um domínio específico e são instalados por várias partes.

## <a name="types-of-cookies"></a>Tipos de cookies

Os tipos de cookie e seus escopos correspondentes são os seguintes:

|Cookie|Escopo|
| ------ | ------ |
|Cookie primário|Um cookie primário é criado por sites que um usuário visita. Ele é usado para salvar dados, como itens de carrinho de compras, credenciais de entrada. Por exemplo, cookies de autenticação e outras análises.|
|Cookie secundário|Um cookie secundário é tecnicamente o mesmo que um cookie primário. A diferença é que os dados são compartilhados com uma outra parte por meio de um contrato de parceria de dados. Por exemplo, [Análise e relatórios do Microsoft Teams](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference). |
|Cookie de terceiros|Um cookie de terceiros é instalado por um domínio diferente daquele que o usuário visitou explicitamente e é usado principalmente para acompanhamento. Por exemplo, os botões **Curtir**, serviço de anúncios e chats ao vivo.|

## <a name="cookies-and-http-requests"></a>Cookies e solicitações HTTP

Antes da introdução das restrições do SameSite, os cookies eram armazenados no navegador. Eles eram anexados a cada solicitação HTTP da Web e enviados ao servidor pelo cabeçalho de resposta HTTP `Set Cookie`. Esse método introduziu vulnerabilidades de segurança, como solicitação intersite forjada, chamadas de ataques CSRF. O componente do SameSite reduziu a exposição por meio de sua implementação e gerenciamento no cabeçalho SetCookie.

## <a name="samesite-cookie-attribute-initial-release"></a>Atributo de cookie SameSite: versão inicial

O Google Chrome versão 51 introduziu a especificação `SetCookie SameSite` como um atributo opcional. A partir do Build 17672, o Windows 10 introduziu o suporte a cookies SameSite no navegador [Microsoft&nbsp; Edge](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/).

Você pode recusar a adição do atributo de cookie SameSite ao cabeçalho `SetCookie` ou adicioná-lo com uma das duas configurações, **Lax** e **Strict**. Um atributo SameSite não implementado foi considerado o estado padrão.

## <a name="samesite-cookie-attribute-2020-release"></a>Atributo de cookie SameSite: versão 2020

O Chrome 80, lançado em fevereiro de 2020, introduziu novos valores de cookie e impõe políticas de cookie por padrão. Três valores são passados para o atributo SameSite atualizado: **Strict**, **Lax** ou **None**. Se não for especificado, o atributo SameSite dos cookies assume o valor `SameSite=Lax` por padrão.

Os atributos do cookie SameSite são os seguintes:

|Setting | Imposição | Valor |Especificação do atributo |
| -------- | ----------- | --------|--------|
| **Lax**  | Os cookies são enviados automaticamente apenas em um contexto **primário** e com solicitações HTTP GET. Os cookies SameSite são retidos em subsolicitações entre sites, como chamadas para carregar imagens ou iframes. Eles são enviados quando um usuário navega pela URL de um site externo, por exemplo, seguindo um link.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Estrito** |O navegador envia apenas cookies para solicitações de contexto primário. Essas são solicitações originadas do site que define o cookie. Se a solicitação tiver sido originada de uma URL diferente da localização atual, nenhum dos cookies marcados com o atributo `Strict` será enviado.| Opcional |`Set-Cookie: key=value; SameSite=Strict`|
| **Nenhum** | Os cookies são enviados em solicitações de contexto primário e entre origens; no entanto, o valor deve ser definido explicitamente como **`None`** e todas as solicitações do navegador **devem seguir o protocolo HTTPS** e incluir o atributo **`Secure`** que requer uma conexão criptografada. Os cookies que não cumprem esse requisito **rejeitados**. <br/>**Ambos os atributos são necessários juntos**. Se **`None`** for especificado sem **`Secure`** ou se o protocolo HTTPS não for usado, os cookies de terceiros serão rejeitados.| Opcional, mas, se definido, o protocolo HTTPS é obrigatório. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Implicações e ajustes do Teams

1. Habilite a configuração relevante do SameSite para seus cookies e certifique-se que seus aplicativos e extensões continuam funcionando no Teams.
1. Se os aplicativos ou extensões falharem, faça as correções necessárias antes da versão do Chrome 80.
1. Os parceiros internos da Microsoft podem ingressar na seguinte equipe para obter mais informações ou ajudar com esse problema: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47>.

> [!NOTE]
> Você deve definir o atributo SameSite para refletir a finalidade para a qual o cookie é usado. Não confie no comportamento padrão do navegador. Para obter mais informações, confira [Desenvolvedores: prepare-se para o novo SameSite=None; Configurações Seguras de Cookie](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Guias, módulos de tarefa e extensões de mensagem

* As guias do Teams usam `<iframes>` para inserir conteúdo que é exibido em um contexto primário ou de nível superior.
* Os módulos de tarefas permitem que você crie experiências pop-up modais em seu aplicativo Teams. Semelhante a uma guia, uma janela modal é aberta dentro da página atual.
* As extensões de mensagem permitem inserir conteúdo enriquecido em uma mensagem de chat a partir de recursos externos.

Todos os cookies usados pelo conteúdo inserido são considerados como de terceiros quando o site é exibido em um `<iframe>`. Além disso, se algum recurso remoto em uma página depender de cookies que são enviados com uma solicitação `<img>` e marcas `<script>`, fontes externas e conteúdo personalizado, você deve garantir que eles sejam marcados para uso entre sites, como `SameSite=None; Secure` ou garantir que um fallback esteja em vigor.

### <a name="authentication"></a>Autenticação

Você deve usar o fluxo de autenticação baseado na Web para o seguinte:

* Páginas de conteúdo inseridas em guias.
* Página de configuração, módulo de tarefa e extensão de mensagem.
* Bot de conversação com um módulo de tarefa.

De acordo com as restrições atualizadas do SameSite, um navegador não adicionará um cookie a um site já autenticado se o link derivar de um site externo. Você deve garantir que os cookies de autenticação estejam marcados para uso entre sites `SameSite=None; Secure` ou verificar se um fallback está em vigor.

## <a name="android-system-webview"></a>Android System WebView

O Android WebView é um componente do sistema Chrome que permite que aplicativos Android exibam o conteúdo da Web. Embora as novas restrições sejam padrão, começando com o Chrome 80, elas não são impostas imediatamente em modos de exibição da Web. Elas serão aplicadas no futuro. Para se preparar, o Android permite que aplicativos nativos definam cookies diretamente por meio da [API CookieManager](https://developer.android.com/reference/android/webkit/CookieManager).

> [!NOTE]
>
> * Você deve declarar cookies primários como `SameSite=Lax` ou `SameSite=Strict`, conforme apropriado.
> * Você deve declarar cookies de terceiros como `SameSite=None; Secure`.

## <a name="see-also"></a>Confira também

* [Exemplos de SameSite](https://github.com/GoogleChromeLabs/samesite-examples)
* [Receitas de cookie SameSite](https://web.dev/samesite-cookie-recipes/)
* [Clientes incompatíveis conhecidos]( https://www.chromium.org/updates/same-site/incompatible-clients)
* [Desenvolvedores: Prepare-se para o Novo SameSite=None; Configurações Seguras de Cookies](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)
* [Próximas Alterações de Cookies do SameSite no ASP.NET e ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
* [Cookies HTTP](https://developer.mozilla.org/docs/Web/HTTP/Cookies)
