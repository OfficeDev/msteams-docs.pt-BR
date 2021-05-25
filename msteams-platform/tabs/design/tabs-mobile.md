---
title: Guias em dispositivos móveis
description: Descreve considerações do desenvolvedor para implementar guias em Microsoft Teams celular.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 41ba96b64bd31f3b226aeba72969bc44c1ae8955
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630653"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

Ao criar um aplicativo Microsoft Teams que inclui uma guia, você deve considerar (e testar) como sua guia funcionará nos clientes android e iOS Microsoft Teams. As seções abaixo delineam alguns dos principais cenários que você precisa considerar.

## <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.

## <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Clientes móveis regularmente precisam funcionar com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com quaisquer tempos de tempo apropriados fornecendo uma mensagem contextual ao usuário. Você também deve ter indicadores de progresso do usuário para fornecer comentários aos usuários sobre processos de longa duração.

## <a name="testing-on-mobile-clients"></a>Testes em clientes móveis

Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela estiver em execução. Recomendamos que você teste em dispositivos de alto e baixo desempenho, incluindo um tablet.

## <a name="distribution"></a>Distribuição

Os aplicativos listados no Teams devem ser aprovados para uso móvel para funcionar corretamente no cliente Teams celular. A disponibilidade e o comportamento de tabulação dependem da aprovação do aplicativo.

### <a name="apps-on-teams-store-approved-for-mobile"></a>Aplicativos no Teams store aprovados para dispositivos móveis

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo é listado no Teams e aprovado para uso móvel:

|Recursos   |Disponibilidade móvel?   |Comportamento móvel|
|----------|-----------|------------|
|Canal <br /> e guia grupo|Sim|A guia é aberta Teams cliente móvel usando a configuração do `contentUrl` aplicativo.|
|Aplicativo pessoal|Sim|Cada guia na guia aplicativo pessoal é aberta no cliente Teams móvel usando sua respectiva `contentUrl` configuração.|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Aplicativos na Teams não aprovados para dispositivos móveis

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo está listado no Teams, mas não aprovado para uso móvel:

| Recursos | Disponibilidade móvel? | Comportamento móvel |
|----------|-----------|------------|
|Guia Canal e grupo|Sim|A guia é aberta no navegador padrão do dispositivo, em vez do cliente Teams móvel usando a configuração do aplicativo, que também deve ser incluído na função do `websiteUrl` `setSettings()` [código-fonte.](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true) No entanto, os usuários ainda podem exibir a guia no cliente Teams móvel selecionando **Mais** ao lado do aplicativo e escolhendo **Abrir**, o que dispara a configuração do `contentUrl` aplicativo.|
|Aplicativo pessoal|Não|Não aplicável|

### <a name="apps-not-on-teams-store"></a>Aplicativos que não Teams loja

Se você estiver fazendo sideload do seu aplicativo ou publicação no catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo Teams aplicativos da loja aprovados pela Microsoft para dispositivos móveis.

## <a name="see-also"></a>Confira também

* [Diretrizes de design de tabulação](~/tabs/design/tabs.md)
