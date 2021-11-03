---
title: Guias em dispositivos móveis
description: Descreve considerações do desenvolvedor para implementar guias em Microsoft Teams celular.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 2b540369b2da9fb0d6eae5d6fd8ddf121992147d
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60719851"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

Ao criar um aplicativo Microsoft Teams que inclui uma guia, você deve testar como sua guia funciona nos clientes android e iOS Microsoft Teams. Este artigo descreve alguns dos principais cenários que você deve considerar.

Se você optar por fazer com que seu canal ou guia de grupo apareça Teams clientes móveis, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade. Para garantir a experiência ideal do usuário, você deve seguir as diretrizes para guias no celular neste artigo ao criar suas guias.

Os [aplicativos distribuídos pelo Teams têm](~/concepts/deploy-and-publish/appsource/publish.md) um processo de aprovação separado para clientes móveis. O comportamento padrão desses aplicativos é o seguinte:

| **Funcionalidade do aplicativo** | **Comportamento se o aplicativo for aprovado** | **Comportamento se o aplicativo não for aprovado** |
| --- | --- | --- |
| **Guias pessoais** | O aplicativo aparece na barra inferior dos clientes móveis. Guias abertas no cliente Teams cliente. | O aplicativo não aparece na barra inferior dos clientes móveis. |
| **Guias de canal e grupo** | A guia é aberta no cliente Teams usando `contentUrl` . | A guia é aberta em um navegador fora do Teams cliente usando `websiteUrl` . |

> [!NOTE]
> * Os aplicativos enviados ao [AppSource](https://appsource.microsoft.com) para publicação no Teams são avaliados automaticamente para a capacidade de resposta móvel. Para qualquer consulta, entre em contato com teamsubm@microsoft.com.
> * Para todos os aplicativos que não são distribuídos por meio do AppSource, as guias são abertas em uma webview no aplicativo dentro dos clientes Teams por padrão e não há um processo de aprovação separado necessário.
> * O comportamento padrão dos aplicativos só será aplicável se for distribuído por meio do Teams store. Por padrão, todas as guias são abertas no Teams cliente.
> * Para iniciar uma avaliação do seu aplicativo para dispositivos móveis, entre em contato com teamsubm@microsoft.com com os detalhes do aplicativo.

## <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.

## <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Os clientes móveis funcionam com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com todos os tempos de tempo apropriados fornecendo uma mensagem contextual ao usuário. Você também deve usar indicadores de progresso para fornecer comentários aos usuários sobre processos de longa duração.

## <a name="testing-on-mobile-clients"></a>Testes em clientes móveis

Você deve validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela estiver em execução. É recomendável que você teste em dispositivos de alto e baixo desempenho, incluindo um tablet.

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
|Guia Canal e grupo|Sim|A guia é aberta no navegador padrão do dispositivo, em vez do cliente Teams móvel usando a configuração do aplicativo, que também deve ser incluído na função `websiteUrl` do código-fonte. `setSettings()` [](/microsoftteams/platform/tabs/how-to/using-teams-client-sdk#settings-namespace) No entanto, os usuários podem exibir a guia Teams cliente móvel selecionando **Mais** ao lado do aplicativo e escolhendo **Abrir**, o que dispara a configuração do `contentUrl` aplicativo.|
|Aplicativo pessoal|Não|Não aplicável|

### <a name="apps-not-on-teams-store"></a>Aplicativos que não Teams loja

Se você estiver fazendo sideload do aplicativo ou publicação no catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo Teams aplicativos da loja aprovados pela Microsoft para dispositivos móveis.

## <a name="see-also"></a>Confira também

* [Diretrizes de design de tabulação](~/tabs/design/tabs.md)
* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)

## <a name="next-step"></a>Próxima Etapa

> [!div class="nextstepaction"]
> [Obtenha contexto para sua guia](~/tabs/how-to/access-teams-context.md)
