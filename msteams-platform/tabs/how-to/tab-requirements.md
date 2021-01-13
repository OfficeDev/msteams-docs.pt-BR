---
title: Noções básicas sobre requisitos de guia
author: laujan
description: Todas as guias do Microsoft Teams devem cumprir esses requisitos.
keywords: canal de grupo de guias do teams configurável
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 1f5a3eaa8ca16878944288d5dbbfa78cfe9fa3ce
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797905"
---
# <a name="tab-requirements"></a>Requisitos de guia

As guias do Teams devem cumprir os seguintes requisitos:

* Você deve permitir que suas páginas de guia sejam fornecidas em um iFrame, por meio de X-Frame-Options e/ou cabeçalhos de resposta HTTP content-security-policy.
  * De definir o header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Para compatibilidade com o Internet Explorer 11, `X-Content-Security-Policy` de definida também.
  * Como alternativa, de definir o header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` . Esse header é preterido, mas ainda é respeitado pela maioria dos navegadores.
* Normalmente, como uma proteção contra a tomada de cliques, as páginas de logon não são renderizações em iFrames. Portanto, sua lógica de autenticação precisa usar um método diferente de redirecionamento (por exemplo, usar autenticação baseada em token ou cookie).

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, apresenta novos valores de cookie e impõe políticas de cookie por padrão. É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. *Veja* [o atributo de cookie SameSite (atualização de 2020).](../../resources/samesite-cookie-update.md)

* Os navegadores aderem a uma restrição de política de mesma origem que impede que uma página da Web faz solicitações a um domínio diferente do que servia uma página da Web. No entanto, talvez seja necessário redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio. A lógica de navegação entre domínios deve permitir que o cliente do Teams valide a origem em relação a uma lista validDomains estática no manifesto do aplicativo ao carregar ou se comunicar com a guia.

* Para criar uma experiência perfeita, você deve criar um estilo para suas guias com base no tema, design e intenção do cliente Teams. Normalmente, as guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentram em um pequeno conjunto de tarefas ou em um subconjunto de dados relevantes para o local do canal da guia.

* Na página de conteúdo, adicione uma referência ao [SDK](/javascript/api/overview/msteams-client) do cliente JavaScript do Microsoft Teams usando marcas de script. Após o carregamento da página, faça uma chamada `microsoftTeams.initialize()` para. Sua página não será exibida se você não o fizer.
