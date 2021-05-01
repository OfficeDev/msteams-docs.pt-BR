---
title: Microsoft Teams e o atributo cookie SameSite (atualização 2020)
author: laujan
description: descreve os atributos do cookie SameSite
keywords: atributos de cookie samesite
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 1841e349f3da61c6f8077e5a56874989aa6212ca
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101811"
---
# <a name="microsoft-teams-and-the-samesite-cookie-attribute-2020-update"></a>Microsoft Teams e o atributo cookie SameSite (atualização 2020)

## <a name="cookies-in-brief"></a>Cookies resumidos

 Cookies são cadeias de caracteres de texto, enviadas de sites e armazenadas em um computador pelo navegador da Web. Eles geralmente são usados para autenticação e personalização, por exemplo, recordando informações de estado, preservando as configurações do usuário, gravando atividades de navegação e exibindo anúncios relevantes. Os cookies são sempre vinculados a um determinado domínio e podem ser instalados por várias partes. Eles são categorizados da seguinte forma:

 |Cookie|Escopo|
 | ------ | ------ |
 |**Cookie de primeira parte**|Um cookie de primeira parte é criado por sites que um usuário visita e é usado para salvar dados, como itens de carrinho de compras, credenciais de logon (por exemplo, cookies de autenticação) e outras análises.|
 |**Cookie de terceiros**|Tecnicamente, os cookies de terceiros são os mesmos de um cookie de primeira parte. A diferença é que os dados são compartilhados com uma segunda parte por meio de um contrato de parceria de dados (por exemplo, Microsoft Teams [análise e relatório](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference)). |
 |**Cookie de terceiros**|Um cookie de terceiros é instalado por um domínio diferente do que o usuário visitou explicitamente e é usado principalmente para controle (por exemplo, botões "Like"), serviço de publicidade e chats ao vivo.|

### <a name="cookies-and-http-requests"></a>Cookies e solicitações HTTP

Antes da introdução das restrições do SameSite, quando os cookies eram armazenados no navegador, eles eram anexados a cada solicitação *da* Web HTTP e enviados ao servidor pelo cabeçalho de resposta HTTP Set-Cookie. Previsivelmente, esse desempenho tinha o potencial de introduzir vulnerabilidades de segurança, como ataques de falsificação de solicitação entre sites (CSRF). *Consulte* [cookies HTTP](https://developer.mozilla.org/docs/Web/HTTP/Cookies). O componente SameSite redução dessa exposição por meio de sua implementação e gerenciamento no header SetCookie.

### <a name="samesite-attribute-initial-release"></a>Atributo SameSite: versão inicial

O Google Chrome versão 51 introduziu a especificação SetCookie SameSite como *um atributo* opcional. A partir do Build 17672, Windows 10 o suporte a cookies SameSite para o [Microsoft Edge navegador](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/).

Os desenvolvedores podem optar por não adicionar o atributo cookie SameSite ao header SetCookie ou eles podem adicioná-lo com uma das duas configurações, *Lax* e *Strict*. Um atributo SameSite não simplificado foi considerado o estado padrão.

## <a name="samesite-cookie-attribute-2020-release"></a>Atributo de cookie SameSite: versão 2020

O Chrome 80, agendado para lançamento em fevereiro de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão. Três valores podem ser passados para o atributo SameSite atualizado: *Strict*, *Lax* ou *None*. Cookies que não especificam o atributo SameSite serão padrão para `SameSite=Lax` .

|Setting | Imposição | Valor |Especificação de Atributo |
| -------- | ----------- | --------|--------|
| **Lax**  | Os cookies serão enviados automaticamente somente em um *contexto de primeira* parte e com solicitações HTTP GET. Os cookies sameSite serão retidos em sub-solicitações entre sites, como chamadas para carregar imagens ou iframes, mas serão enviados quando um usuário navegar para a URL de um site externo, por exemplo, seguindo um link.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Estrito** |O navegador só enviará cookies para solicitações de contexto de primeira parte (solicitações provenientes do site que definiram o cookie). Se a solicitação tiver sido originada de uma URL diferente da do local atual, nenhum dos cookies marcados com o `Strict` atributo será enviado.| Opcional |`Set-Cookie: key=value; SameSite=Strict`|
| **Nenhum** | Os cookies serão enviados no contexto de primeira parte e em solicitações de origem cruzada; no entanto, o valor deve ser definido explicitamente como e todas as solicitações de navegador devem seguir o protocolo HTTPS e incluir o atributo que exige uma **`None`** conexão  **`Secure`** criptografada. Cookies que não aderem a esse requisito serão **rejeitados.** <br/>**Ambos os atributos são necessários juntos.** Se apenas for especificado sem ou se o **`None`** protocolo HTTPS não for usado, o cookie de terceiros **`Secure`**  será rejeitado.| Opcional, mas, se definido, o protocolo HTTPS é necessário. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Teams implicações e ajustes

1. Habilita a configuração relevante do SameSite para seus cookies e valide se seus aplicativos e extensões continuam a funcionar em Teams.
1. Se seus aplicativos ou extensões falharem, faça as correções necessárias antes da versão do Chrome 80.
1. Os parceiros internos da Microsoft podem ingressar na seguinte equipe se precisarem de mais informações ou ajudar com este problema: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47> .

> [!NOTE]
> Para prática recomendada, é recomendável que você sempre desem conjunto de atributos SameSite para refletir o uso pretendido para seus cookies. Não confie no comportamento padrão do navegador. Para obter mais informações, consulte [Desenvolvedores: Prepare-se para New SameSite=None; Cookies seguros Configurações](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Guias, módulos de tarefa e extensões de mensagem

* Teams guias usam para incorporar conteúdo que é exibido em um contexto de nível superior `<iframes>` ou de primeira parte.
* Os módulos de tarefas permitem que você crie experiências pop-up modais em seu aplicativo Teams. Semelhante a uma guia, uma janela modal é aberta dentro da página atual.
* As extensões de mensagem permitem inserir conteúdo enriquecido na mensagem de chat de recursos externos.

Todos os cookies usados pelo conteúdo incorporado serão considerados de terceiros quando o site for exibido em `<iframe>` um . Além disso, se qualquer recurso remoto em uma página depender de cookies que estão sendo enviados com uma solicitação e marcas, fontes externas e conteúdo personalizado, você deve garantir que eles sejam marcados para uso entre sites, como ou garantir que um fallback está `<img>` `<script>` no `SameSite=None; Secure` local.

### <a name="authentication"></a>Autenticação

* Se você exigir autenticação para páginas de conteúdo incorporado em guias, precisará usar o fluxo de autenticação baseado na Web.
* Um fluxo de autenticação baseado na Web também pode ser usado para uma página de configuração, módulo de tarefa ou extensão de mensagens.
* Você pode usar um fluxo de autenticação baseado na Web para um bot de conversa. Você precisará usar um módulo de tarefa.

De acordo com as restrições atualizadas do SameSite, um navegador não adicionará um cookie a um site já autenticado se o link derivar de um site externo. Você precisará garantir que seus cookies de autenticação sejam marcados para uso entre sites — ou garantir `SameSite=None; Secure` que um fallback está no local.

### <a name="android-system-webview"></a>Android System WebView

O Android WebView é um componente do sistema Chrome que permite que aplicativos Android exibem conteúdo da Web. Embora as novas restrições se tornem o padrão, começando com o Chrome 80, elas não serão impostas imediatamente em WebViews. Eles serão aplicados no futuro. Para se preparar, o Android permite que aplicativos nativos de definir cookies diretamente por meio da [API CookeManager](https://developer.android.com/reference/android/webkit/CookieManager):

* Para cookies que são necessários apenas em um contexto de primeira parte, você deve declare-os como `SameSite=Lax` ou `SameSite=Strict` , conforme apropriado.
* Para cookies necessários em um contexto de terceiros, você deve garantir que eles sejam declarados como `SameSite=None; Secure` .

## <a name="learn-more"></a>Saiba mais

* [Exemplos de SameSite](https://github.com/GoogleChromeLabs/samesite-examples)

* [Receitas de cookie sameSite](https://web.dev/samesite-cookie-recipes/)

* [Clientes incompatíveis conhecidos]( https://www.chromium.org/updates/same-site/incompatible-clients)

* [Desenvolvedores: Prepare-se para o novo SameSite=None; Cookies seguros Configurações](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)

**Impacto Conexão OpenId**<br>
[Alterações futuras do cookie samesite no ASP.NET e ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
