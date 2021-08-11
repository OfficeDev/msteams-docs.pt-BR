---
title: Pré-requisitos
author: surbhigupta
description: Todas as guias Microsoft Teams devem seguir esses requisitos.
keywords: canal de grupo de guias do teams configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 36d5a6ee785779c8ba186a00ec80519a189ac278e7ec2298bba82fb53f0a848a
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57701797"
---
# <a name="prerequisites"></a>Pré-requisitos

Teams guias devem seguir os seguintes pré-requisitos:

* Você deve permitir que suas páginas de tabulação sejam mostradas em um iFrame, usando cabeçalhos de resposta HTTP X-Frame-Options e Content-Security-Policy.
  * Definir o header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Para compatibilidade com o Internet Explorer 11, de definir `X-Content-Security-Policy` .
  * Como alternativa, de definir o header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` . Esse header é preterido, mas ainda é aceito pela maioria dos navegadores.

* Normalmente, como uma proteção contra o clickjacking, as páginas de logon não são renderizações em iFrames. Sua lógica de autenticação precisa usar um método diferente de redirecionamento. Por exemplo, use autenticação baseada em token ou cookie.

    > [!NOTE]
    > O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão. É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. Para obter mais informações, consulte [atributo cookie SameSite](../../resources/samesite-cookie-update.md).

* Os navegadores aderem a uma restrição de política de mesma origem. Ele impede que as páginas da Web fazem solicitações para domínios diferentes da página da Web atendida. No entanto, você pode redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio. Sua lógica de navegação entre domínios deve permitir que o cliente Teams valide a origem em relação a uma lista estática no manifesto do aplicativo ao carregar ou se comunicar `validDomains` com a guia.

* Você deve estilar suas guias com base Teams tema, design e intenção do cliente. Normalmente, as guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou em um subconjunto de dados relevante para o local do canal da guia.

* Em sua página de conteúdo, adicione uma referência ao [Microsoft Teams SDK](/javascript/api/overview/msteams-client) do cliente JavaScript usando marcas de script. Depois que sua página for carregada, faça uma chamada `microsoftTeams.initialize()` para , caso contrário, sua página não será exibida.

* Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.

* Se você optar por fazer com que seu canal ou guia de grupo apareça Teams clientes móveis, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade.

* A guia Teams MS não dá suporte à capacidade de carregar sites da intranet que usam certificados auto-assinados.

## <a name="tools-you-can-use-to-build-tabs"></a>Ferramentas que você pode usar para criar guias
* [Kit de ferramentas do Teams para Visual Studio Code](../../toolkit/visual-studio-code-overview.md)
* [Kit de ferramentas do Teams para Visual Studio](../../toolkit/visual-studio-overview.md)

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar seu primeiro aplicativo usando o Node.js](../../get-started/first-app-react.md)
* [Criar seu primeiro aplicativo usando o Blazor](../../get-started/first-app-blazor.md)
* [Criar seu primeiro aplicativo usando o SPFx](../../get-started/first-app-spfx.md)
* [Criar o seu primeiro bot de conversação para o Microsoft Teams](../../get-started/first-app-bot.md)
* [Criar sua primeira extensão de mensagem](../../get-started/first-message-extension.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
