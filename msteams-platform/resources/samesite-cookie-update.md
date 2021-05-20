---
title: Microsoft Teams e o atributo de cookie SameSite (atualização 2020)
author: laujan
description: descreve os atributos do cookie SameSite
keywords: cookie atributos mesmo
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: cf28a28050d50b2b6b2601a3231cdad30211ab2c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566709"
---
# <a name="microsoft-teams-and-the-samesite-cookie-attribute-2020-update"></a>Microsoft Teams e o atributo de cookie SameSite (atualização 2020)

## <a name="cookies-in-brief"></a>Cookies em breve

 Cookies são strings de texto, enviados de sites e armazenados em um computador pelo navegador da Web. Eles são normalmente usados para autenticação e personalização, por exemplo, recordando informações imponentes, preservando configurações do usuário, registrando atividades de navegação e exibindo anúncios relevantes. Os cookies estão sempre vinculados a um determinado domínio e podem ser instalados por várias partes. Eles são categorizados da seguinte forma:

 |Cookie|Escopo|
 | ------ | ------ |
 |**Biscoito de primeira festa**|Um cookie de primeira parte é criado por sites que um usuário visita e é usado para salvar dados, como itens de carrinho de compras, credenciais de login. Por exemplo, cookies de autenticação e outras análises.|
 |**Biscoito de segunda parte**|Um biscoito de segunda parte é tecnicamente o mesmo que um biscoito de primeira festa. A diferença é que os dados são compartilhados com uma segunda parte através de um acordo de parceria de dados. Por exemplo, [Microsoft Teams análises e relatórios](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference). |
 |**Biscoito de terceiros**|Um cookie de terceiros é instalado por um domínio diferente do que o usuário visitou explicitamente e é usado principalmente para rastreamento. Por exemplo, botões "Curtir", serviços de anúncios e bate-papos ao vivo.|

### <a name="cookies-and-http-requests"></a>Cookies e solicitações HTTP

Antes da introdução das restrições do SameSite, quando os cookies eram armazenados no navegador, eles eram anexados a *todas as* solicitações da Web HTTP e enviados ao servidor pelo cabeçalho de resposta HTTP Set-Cookie. Previsivelmente, esse desempenho tinha o potencial de introduzir vulnerabilidades de segurança, como ataques de Falsificação de Solicitações de Sites Cruzados (CSRF). *Consulte* [cookies HTTP](https://developer.mozilla.org/docs/Web/HTTP/Cookies). O componente SameSite mitigau essa exposição através de sua implementação e gerenciamento no cabeçalho SetCookie.

### <a name="samesite-attribute-initial-release"></a>Atributo SameSite: lançamento inicial

O Google Chrome versão 51 introduziu a especificação SetCookie SameSite como um atributo *opcional.* Começando pela Build 17672, Windows 10 introduziu o suporte a cookies SameSite para o [navegador Microsoft Edge](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/).

Os desenvolvedores podem optar por não adicionar o atributo de cookie SameSite ao cabeçalho SetCookie ou eles poderiam adicioná-lo com uma das duas configurações, *Lax* e *Strict*. Um atributo SameSite não-plementado foi considerado o estado padrão.

## <a name="samesite-cookie-attribute-2020-release"></a>Atributo do cookie SameSite: lançamento de 2020

O Chrome 80, com lançamento previsto para fevereiro de 2020, introduz novos valores de cookies e impõe políticas de cookies por padrão. Três valores podem ser passados para o atributo SameSite atualizado: *Strict*, *Lax*, or *None*. Cookies que não especificam o atributo SameSite serão padrão para `SameSite=Lax` .

|Configuração | execução | Valor |Especificação de atributo |
| -------- | ----------- | --------|--------|
| **frouxo**  | Os cookies serão enviados automaticamente apenas em um contexto *de primeira parte* e com solicitações HTTP GET. Os cookies sameSite serão retidos em sub-solicitações entre sites, como chamadas para carregar imagens ou iframes, mas serão enviados quando um usuário navegar para a URL de um site externo, por exemplo, seguindo um link.| **Padrão** |`Set-Cookie: key=value; SameSite=Lax`|
| **estrito** |O navegador só enviará cookies para solicitações de contexto de primeira parte (solicitações originárias do site que definem o cookie). Se a solicitação se originou de uma URL diferente da localização atual, nenhum dos cookies marcados com o `Strict` atributo será enviado.| Opcional |`Set-Cookie: key=value; SameSite=Strict`|
| **Nenhum** | Os cookies serão enviados tanto no contexto da primeira parte quanto nas solicitações de origem cruzada; no entanto, o valor deve ser explicitamente definido **`None`** e todas as solicitações do navegador devem **seguir o protocolo HTTPS** e incluir o atributo que requer **`Secure`** uma conexão criptografada. Cookies que não aderirem a esse requisito serão **rejeitados**. <br/>**Ambos os atributos são necessários em conjunto.** Se apenas **`None`** for especificado sem ou se o protocolo HTTPS não for **`Secure`**  usado, o cookie de terceiros será rejeitado.| Opcional, mas, se definido, o protocolo HTTPS é necessário. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Teams implicações e ajustes

1. Habilite a configuração relevante do SameSite para seus cookies e valide que seus aplicativos e extensões continuam funcionando em Teams.
1. Se seus aplicativos ou extensões falharem, faça as correções necessárias antes da versão do Chrome 80.
1. Os parceiros internos da Microsoft podem se juntar à seguinte equipe se precisarem de mais informações ou ajudarem com esse problema: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47> .

> [!NOTE]
> Para as melhores práticas, recomenda-se que você sempre defina atributos SameSite para refletir o uso pretendido para seus cookies. Não confie no comportamento padrão do navegador. Para obter mais informações, consulte [Desenvolvedores: Prepare-se para novo SameSite=None; Configurações de biscoito seguro](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Guias, módulos de tarefas e extensões de mensagens

* Teams guias de pesquisa `<iframes>` são usados para incorporar conteúdo que seja visualizado em um contexto de alto nível ou de primeira parte.
* Os módulos de tarefas permitem que você crie experiências pop-up modais em seu aplicativo Teams. Semelhante a uma guia, uma janela modal é aberta dentro da página atual.
* As extensões de mensagens permitem inserir conteúdo enriquecido na mensagem de bate-papo a partir de recursos externos.

Quaisquer cookies usados por conteúdo incorporado serão considerados terceiros quando o site for exibido em um `<iframe>` . Além disso, se quaisquer recursos remotos em uma página dependem de cookies sendo enviados com uma solicitação `<img>` e `<script>` tags, fontes externas e conteúdo personalizado, você deve garantir que eles estejam marcados para uso entre sites, como `SameSite=None; Secure` ou garantir que um recuo esteja no lugar.

### <a name="authentication"></a>Autenticação

* Se você precisar de autenticação para páginas de conteúdo incorporadas em guias, você precisará usar o fluxo de autenticação baseado na Web.
* Um fluxo de autenticação baseado na Web também pode ser usado para uma página de configuração, módulo de tarefa ou extensão de mensagens.
* Você pode usar um fluxo de autenticação baseado na Web para um bot de conversação que você precisará para usar um módulo de tarefa.

De acordo com as restrições atualizadas do SameSite, um navegador não adicionará um cookie a um site já autenticado se o link derivar de um site externo. Você precisará garantir que seus cookies de autenticação estejam marcados para uso entre sites `SameSite=None; Secure` — ou garantir que um recuo esteja no lugar.

### <a name="android-system-webview"></a>WebView do sistema Android

Android WebView é um componente do sistema Chrome que permite que aplicativos Android exibam conteúdo web. Embora as novas restrições se tornem padrão, começando pelo Chrome 80, elas não serão imediatamente aplicadas no WebViews. Eles serão aplicados no futuro. Para se preparar, o Android permite que aplicativos nativos despem cookies diretamente através da [API CookeManager](https://developer.android.com/reference/android/webkit/CookieManager):

* Para cookies que só são necessários em um contexto de primeira parte, você deve declará-los como `SameSite=Lax` ou `SameSite=Strict` , conforme apropriado.
* Para cookies necessários em um contexto de terceiros, você deve garantir que eles sejam declarados como `SameSite=None; Secure` .

## <a name="see-also"></a>Confira também

* [Exemplos do SameSite](https://github.com/GoogleChromeLabs/samesite-examples)

* [Receitas de biscoito SameSite](https://web.dev/samesite-cookie-recipes/)

* [Clientes incompatíveis conhecidos]( https://www.chromium.org/updates/same-site/incompatible-clients)

* [Desenvolvedores: Preparem-se para o novo SameSite=None; Configurações de biscoito seguro](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)

**Impacto Conexão OpenId**<br>
[Próximas alterações de cookies do Mesmosite em ASP.NET e ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
