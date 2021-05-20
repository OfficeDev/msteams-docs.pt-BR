---
title: Entendendo os requisitos da guia
author: laujan
description: Todas as guias Microsoft Teams devem aderir a esses requisitos.
keywords: equipes guias canal grupo configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a46a80401b29b5436807c9a5b94580beca3786f0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566660"
---
# <a name="tab-requirements"></a>Requisitos de tabulação

Teams guias devem ser respeitadas aos seguintes requisitos:

* Você deve permitir que suas páginas de guia sejam servidas em um iFrame, através de cabeçalhos de resposta HTTP X-Frame-Options e/ou Content-Security-Policy..
  * Definir cabeçalho: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Para compatibilidade com o Internet Explorer 11, também `X-Content-Security-Policy` seja.
  * Alternativamente, definir cabeçalho `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` . Este cabeçalho é preterido, mas ainda respeitado pela maioria dos navegadores.
* Normalmente, como uma proteção contra o jacking de cliques, as páginas de login não são renderizadas em iFrames. Portanto, sua lógica de autenticação precisa usar um método diferente do redirecionamento. Por exemplo, use autenticação baseada em tokens ou cookie.

> [!NOTE]
> O Chrome 80, com lançamento previsto para o início de 2020, introduz novos valores de cookies e impõe políticas de cookies por padrão. Recomenda-se que você defina o uso pretendido para seus cookies em vez de confiar no comportamento padrão do navegador. Para obter mais informações, consulte [o atributo cookie SameSite (atualização 2020)](../../resources/samesite-cookie-update.md).

* Os navegadores aderem a uma restrição de política de mesma origem que impede uma página da Web de fazer solicitações para um domínio diferente daquele que serviu uma página da Web. No entanto, você pode precisar redirecionar a configuração ou a página de conteúdo para um outro domínio ou subdomínio. Sua lógica de navegação entre domínios deve permitir que o cliente Teams valide a origem contra uma lista de códigos de validação estática no manifesto do aplicativo ao carregar ou se comunicar com a guia.

* Para criar uma experiência perfeita, você deve estilizar suas guias com base no tema, design e intenção do Teams cliente. Normalmente, as guias funcionam melhor quando são construídas para atender a uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou um subconjunto de dados relevantes para a localização do canal da guia.

* Na sua página de conteúdo, adicione uma referência ao [Microsoft Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client) usando tags de script. Seguindo a carga da página, faça uma chamada para `microsoftTeams.initialize()` . Sua página não será exibida se você não fizer isso.

* Para que a autenticação funcione em clientes móveis, você deve atualizá-lo Teams JavaScript SDK para pelo menos a versão 1.4.1.

* Se você optar por ter seu canal ou aba de grupo aparecendo em Teams clientes móveis, a `setSettings()` configuração deve ter um valor para o `websiteUrl` imóvel.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Crie uma guia pessoal personalizada usando Node.js e o Gerador Yeoman para Microsoft Teams](~/tabs/quickstarts/create-personal-tab-node-yeoman.md)