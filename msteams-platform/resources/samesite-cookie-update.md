---
title: Microsoft Teams e o atributo de cookie SameSite (atualização 2020)
author: laujan
description: ''
keywords: atributos de cookies SameSite
ms.topic: reference
ms.author: lomeybur
ms.openlocfilehash: 167266ba0b5af1c8233cffe1fef496dd94c27ae4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672477"
---
# <a name="microsoft-teams-and-the-samesite-cookie-attribute-2020-update"></a>Microsoft Teams e o atributo de cookie SameSite (atualização 2020)

## <a name="cookies-in-brief"></a>Cookies em breve

 Cookies são cadeias de caracteres de texto, enviadas de sites e armazenadas em um computador pelo navegador da Web. Normalmente, eles são usados para autenticação e personalização, por exemplo, recuperar informações monitoradas, preservar as configurações do usuário, registrar a atividade de navegação e exibir anúncios relevantes. Os cookies sempre estão vinculados a um domínio específico e podem ser instalados por várias partes. Eles são categorizados da seguinte maneira:

 |Cookie|Escopo|
 | ------ | ------ |
 |**Cookie primário**|Um cookie primário é criado por sites que um usuário visita e é usado para salvar dados como itens de carrinho de compras, credenciais de logon (por exemplo, cookies de autenticação) e outras análises.|
 |**Cookie de terceiros**|Os cookies de terceiros é tecnicamente o mesmo que um cookie de terceiros. A diferença é que os dados são compartilhados com um segundo por meio de um contrato de parceria de dados (por exemplo, [análises e relatórios do Microsoft Teams](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference)). |
 |**Cookie de terceiros**|Um cookie de terceiros é instalado por um domínio diferente daquele que o usuário visitou explicitamente e é usado principalmente para acompanhamento (por exemplo, botões "como"), serviço de anúncios e bate-papos ao vivo.|

### <a name="cookies-and-http-requests"></a>Cookies e solicitações HTTP

Antes da introdução de restrições de SameSite, quando os cookies foram armazenados no navegador, foram anexados a *cada* solicitação Web http e enviados ao servidor pelo cabeçalho de resposta http Set-cookie. Previsível, esse desempenho tinha o potencial de introduzir vulnerabilidades de segurança, como ataques de falsificação de solicitação entre sites (CSRF). *Consulte* [http cookies](https://developer.mozilla.org/docs/Web/HTTP/Cookies). O componente SameSite reduziu essa exposição por meio de sua implementação e gerenciamento no cabeçalho SetCookie.

### <a name="samesite-attribute-initial-release"></a>Atributo SameSite: versão inicial

O Google Chrome versão 51 introduziu a especificação SetCookie SameSite como um atributo *opcional* . A partir da compilação 17672, o Windows 10 introduziu o suporte a cookies SameSite para o [navegador Microsoft Edge](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/).

Os desenvolvedores podem optar por adicionar o atributo de cookie SameSite ao cabeçalho SetCookie ou adicioná-lo a uma das duas configurações, *LAX* e *Strict*. Um atributo SameSite não implementado foi considerado o estado padrão.

## <a name="samesite-cookie-attribute-2020-release"></a>Atributo de cookie SameSite: versão 2020

O Chrome 80, agendado para lançamento em fevereiro de 2020, apresenta novos valores de cookie e impõe políticas de cookies por padrão. Três valores podem ser passados para o atributo SameSite atualizado: *estrito*, *LAX*ou *nenhum*. Os cookies que não especificam o atributo SameSite será `SameSite=Lax`o padrão.

|Setting | Órgão | Valor |Especificação de atributo |
| -------- | ----------- | --------|--------|
| **Relaxar**  | Os cookies serão enviados automaticamente somente em um contexto *primário* e com solicitações HTTP Get. Os cookies do SameSite serão retidos em subprocessos entre sites, como chamadas para carregar imagens ou IFrames, mas serão enviados quando um usuário navegar para a URL de um site externo, por exemplo, seguindo um link.| **Padrão** |`Set-Cookie: key=value; SameSite=Lax`|
| **Impede** |O navegador só enviará cookies para solicitações de contexto de primeiro parceiro (solicitações originadas do site que definem o cookie). Se a solicitação tiver sido originada de uma URL diferente da do local atual, nenhum dos cookies marcados com o `Strict` atributo será enviado.| Opcional |`Set-Cookie: key=value; SameSite=Strict`|
| **Nenhum** | Os cookies serão enviados tanto para as solicitações de contexto de terceiros quanto entre origens; no entanto, o valor deve ser explicitamente **`None`** definido como e todas as solicitações do navegador **devem seguir o protocolo HTTPS** e incluir o **`Secure`** atributo que requer uma conexão criptografada. Os cookies que não estão de acordo com esse requisito serão **rejeitados**. <br/>**Os dois atributos são obrigatórios juntos**. Se apenas **`None`** for especificado sem **`Secure`** ou se o protocolo HTTPS não for usado, o cookie de terceiros será rejeitado.| Opcional, mas, se definido, o protocolo HTTPS é necessário. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="handling-incompatible-clients"></a>Manipulação de clientes incompatíveis

> [!IMPORTANT]
> No momento `SameSite=None` , o cliente da área de trabalho do Microsoft [**Teams**](/aspnet/core/security/samesite?view=aspnetcore-3.1#test-with-electron) ou versões mais antigas do Chrome ou Safari não oferecem suporte a ele. *Consulte* [clientes incompatíveis conhecidos]( https://www.chromium.org/updates/same-site/incompatible-clients).
>No entanto, há duas **soluções alternativas**:
>
>1. Verifique o agente de usuário para fornecer a propriedade SameSite correta. Você pode implementar a verificação de agente de usuário em [**C#**](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/) e [**node. js**](https://web.dev/samesite-cookie-recipes/).
>2. Defina seus atributos de cookies usando os modelos novos e antigos. *Consulte* [tratamento de clientes incompatíveis](https://web.dev/samesite-cookie-recipes/#handling-incompatible-clients)<br><br>
>**Se seu aplicativo estiver em execução no cliente do teams desktop e você definir o atributo SameSite `SameSite=None` como, seu aplicativo não funcionará conforme o esperado.**

O uso de uma das abordagens garantirá que o aplicativo continue funcionando adequadamente quando o cliente da área de trabalho `SameSite=None` do teams for atualizado para uma versão compatível do Chromium.

## <a name="teams-implications-and-adjustments"></a>Implicações e ajustes do teams

>[!WARNING]
>**Os aplicativos executados no cliente do teams desktop são incompatíveis `SameSite=None` com o atributo e não funcionarão conforme o esperado.** Confira as **soluções alternativas**acima.

1. Habilite a configuração do SameSite relevante para seus cookies e valide se seus aplicativos e extensões continuam a trabalhar no Microsoft Teams.
1. Se seus aplicativos ou extensões falharem, faça as correções necessárias antes da versão do Chrome 80.
1. Os parceiros internos da Microsoft podem participar da seguinte equipe se precisarem de mais informações ou ajuda com <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47>esse problema:.

> [!NOTE]
> Para obter uma prática recomendada, é recomendável que você sempre defina os atributos de SameSite para refletir o uso pretendido para seus cookies, não confie no comportamento padrão do navegador. *Consulte* [desenvolvedores: preparar para Nova SameSite = nenhum; Configurações de cookies seguros](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Guias, módulos de tarefas e extensões de mensagens

* As guias do `<iframes>` Teams usam para inserir conteúdo que é exibido em um contexto de nível superior ou primário.
* Os módulos de tarefas permitem que você crie experiências pop-up restritas em seu aplicativo do Microsoft Teams. Semelhante a uma guia, uma janela modal é aberta dentro da página atual.
* As extensões de mensagem permitem que você insira conteúdo aprimorado na mensagem de chat de recursos externos.

Todos os cookies usados pelo conteúdo incorporado serão considerados terceiros quando o site for exibido em um `<iframe>`. Além disso, se qualquer recurso remoto em uma página depender de cookies que estão sendo enviados com uma solicitação (por `<img>` exemplo `<script>` , marcas, fontes externas e conteúdo personalizado), você precisará garantir que eles estejam marcados para uso entre sites — `SameSite=None; Secure` ou garantir que um fallback esteja em vigor.

### <a name="authentication"></a>Autenticação

* Se você precisar de autenticação para páginas de conteúdo incorporadas em guias, será necessário usar o fluxo de autenticação baseado na Web.
* Um fluxo de autenticação baseado na Web também pode ser usado para uma página de configuração, módulo de tarefa ou extensão de mensagens.
* Você pode usar um fluxo de autenticação baseado na Web para um bot de conversa, você precisará usar um módulo de tarefa.

De acordo com as restrições de SameSite atualizadas, um navegador não adicionará um cookie a um site já autenticado se o link for derivado de um site externo. Você precisará garantir que seus cookies de autenticação estejam marcados para uso entre sites — `SameSite=None; Secure` ou garantir que um fallback esteja no local.

### <a name="android-system-webview"></a>WebView do sistema Android

O Android WebView é um componente do sistema Chrome que permite que aplicativos Android exibam conteúdo da Web. Enquanto as novas restrições se tornarão o padrão, começando com o Chrome 80, elas não serão aplicadas imediatamente em webviews. Eles serão aplicados no futuro. Para preparar, o Android permite que aplicativos nativos definam cookies diretamente por meio da [API CookeManager](https://developer.android.com/reference/android/webkit/CookieManager):

* Para cookies que são necessários apenas em um contexto primário, você deve declará-los como `SameSite=Lax` ou `SameSite=Strict`, conforme apropriado.
* Para cookies necessários em um contexto de terceiros, você deve garantir que eles sejam declarados `SameSite=None; Secure`como.

## <a name="learn-more"></a>Saiba mais

[Exemplos de SameSite](https://github.com/GoogleChromeLabs/samesite-examples)

[Receitas de cookies SameSite](https://web.dev/samesite-cookie-recipes/)

[Clientes incompatíveis conhecidos]( https://www.chromium.org/updates/same-site/incompatible-clients)

[Desenvolvedores: Prepare-se para a nova SameSite = nenhum; Configurações de cookies seguros](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)

**Impacto de conexão OpenId**<br>
[Futuras alterações de cookies do SameSite no ASP.NET e no ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
