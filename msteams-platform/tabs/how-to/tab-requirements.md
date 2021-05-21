---
title: Noções básicas sobre os requisitos da guia
author: laujan
description: Todas as guias Microsoft Teams devem seguir esses requisitos.
keywords: canal de grupo de guias do teams configurável
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

Teams guias devem seguir os seguintes requisitos:

* Você deve permitir que suas páginas de tabulação sejam atendidas em um iFrame, por meio de cabeçalhos de resposta HTTP X-Frame-Options e/ou Content-Security-Policy.
  * Definir o header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Para compatibilidade com o Internet Explorer 11, de definir `X-Content-Security-Policy` também.
  * Como alternativa, de definir o header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` . Esse header é preterido, mas ainda é respeitado pela maioria dos navegadores.
* Normalmente, como uma proteção contra o uso de cliques, as páginas de logon não são renderizações em iFrames. Portanto, sua lógica de autenticação precisa usar um método diferente de redirecionamento. Por exemplo, use autenticação baseada em token ou cookie.

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão. É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. Para obter mais informações, consulte [Atributo de cookie sameSite (atualização 2020)](../../resources/samesite-cookie-update.md).

* Os navegadores aderem a uma restrição de política de mesma origem que impede uma página da Web de fazer solicitações para um domínio diferente do que aquele que atendeu a uma página da Web. No entanto, talvez seja necessário redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio. Sua lógica de navegação entre domínios deve permitir que o cliente Teams valide a origem em relação a uma lista validDomains estática no manifesto do aplicativo ao carregar ou se comunicar com a guia.

* Para criar uma experiência perfeita, você deve projetar suas guias com base Teams tema, design e intenção do cliente. Normalmente, as guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou em um subconjunto de dados relevante para o local do canal da guia.

* Em sua página de conteúdo, adicione uma referência ao [Microsoft Teams SDK](/javascript/api/overview/msteams-client) do cliente JavaScript usando marcas de script. Após o carregamento da página, faça uma chamada para `microsoftTeams.initialize()` . Sua página não será exibida se você não o fizer.

* Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.

* Se você optar por fazer com que seu canal ou guia de grupo apareça Teams clientes móveis, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Crie uma guia pessoal personalizada usando Node.js e o Gerador Yeoman para Microsoft Teams](~/tabs/quickstarts/create-personal-tab-node-yeoman.md)