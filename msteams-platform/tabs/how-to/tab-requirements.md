---
title: Noções básicas sobre os requisitos da guia
author: laujan
description: Todas as guias do Microsoft Teams devem cumprir esses requisitos.
keywords: canal de grupo de guias do teams configurável
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 087f894bd2a0a2c7a79e683f504e2c2f5a50c287
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034660"
---
# <a name="tab-requirements"></a>Requisitos de tabulação

As guias do Teams devem seguir os seguintes requisitos:

* Você deve permitir que suas páginas de tabulação sejam atendidas em um iFrame, por meio de cabeçalhos de resposta HTTP X-Frame-Options e/ou Content-Security-Policy.
  * Definir o header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Para compatibilidade com o Internet Explorer 11, de definir `X-Content-Security-Policy` também.
  * Como alternativa, de definir o header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` . Esse header é preterido, mas ainda é respeitado pela maioria dos navegadores.
* Normalmente, como uma proteção contra o uso de cliques, as páginas de logon não são renderizações em iFrames. Portanto, sua lógica de autenticação precisa usar um método diferente de redirecionamento (por exemplo, usar autenticação baseada em token ou baseada em cookie).

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão. É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. *Consulte* [o atributo cookie SameSite (atualização 2020)](../../resources/samesite-cookie-update.md).

* Os navegadores aderem a uma restrição de política de mesma origem que impede uma página da Web de fazer solicitações para um domínio diferente do que aquele que atendeu a uma página da Web. No entanto, talvez seja necessário redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio. Sua lógica de navegação entre domínios deve permitir que o cliente do Teams valide a origem em relação a uma lista validDomains estática no manifesto do aplicativo ao carregar ou se comunicar com a guia.

* Para criar uma experiência perfeita, você deve projetar suas guias com base no tema, design e intenção do cliente teams. Normalmente, as guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou em um subconjunto de dados relevante para o local do canal da guia.

* Em sua página de conteúdo, adicione uma referência ao [SDK](/javascript/api/overview/msteams-client) do cliente JavaScript do Microsoft Teams usando marcas de script. Após o carregamento da página, faça uma chamada para `microsoftTeams.initialize()` . Sua página não será exibida se você não o fizer.

* Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK JavaScript do Teams para pelo menos a versão 1.4.1.

* Se você optar por que seu canal ou guia de grupo apareça em clientes móveis do Teams, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade.