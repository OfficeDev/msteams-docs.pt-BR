---
title: Guias em dispositivos móveis
description: Neste módulo, saiba mais sobre como implementar guias no Microsoft Teams mobile, sua autenticação, conexão de baixa largura de banda, testes em clientes móveis, distribuição e muito mais.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: da9757ee0153b3f2fe80e576e156f45bc90a15cd
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144261"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

Ao criar um aplicativo Microsoft Teams que inclui uma guia, você deve testar como sua guia funciona nos clientes Android e iOS Microsoft Teams cliente. Este artigo descreve alguns dos principais cenários que você deve considerar.

Se você optar por exibir sua guia de canal ou grupo Teams clientes móveis, [`setSettings()`](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-settings-setsettings&preserve-view=true) a configuração deverá ter um valor para a `websiteUrl` propriedade. Para garantir a experiência ideal do usuário, você deve seguir as diretrizes para guias sobre dispositivos móveis neste artigo ao criar suas guias.

Os [aplicativos distribuídos por meio da Teams têm](~/concepts/deploy-and-publish/appsource/publish.md) um processo de aprovação separado para clientes móveis. O comportamento padrão desses aplicativos é o seguinte:

| **Funcionalidade do aplicativo** | **Comportamento se o aplicativo for aprovado** | **Comportamento se o aplicativo não for aprovado** |
| --- | --- | --- |
| **Guias pessoais** | O aplicativo aparece na barra inferior dos clientes móveis. As guias são abertas no Teams cliente. | O aplicativo não aparece na barra inferior dos clientes móveis. |
| **Guias de canal e grupo** | A guia é aberta no cliente Teams usando `contentUrl`. | A guia é aberta em um navegador fora do Teams usando `websiteUrl`. |

> [!NOTE]
>
> * Os aplicativos enviados ao [AppSource](https://appsource.microsoft.com) para publicação no Teams são avaliados automaticamente quanto à capacidade de resposta móvel. Para qualquer consulta, entre em contato com teamsubm@microsoft.com.
> * Para todos os aplicativos que não são distribuídos por meio do AppSource, as guias são abertas em um modo de exibição da Web no aplicativo dentro dos clientes do Teams por padrão e não há nenhum processo de aprovação separado necessário.
> * O comportamento padrão dos aplicativos só será aplicável se for distribuído por meio da Teams armazenamento. Por padrão, todas as guias são abertas no Teams cliente.
> * Para iniciar uma avaliação do seu aplicativo para fins de amizade móvel, entre em contato com teamsubm@microsoft.com com os detalhes do aplicativo.

## <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK do JavaScript para pelo menos a versão 1.4.1.

## <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Os clientes móveis funcionam com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com os tempos limite adequadamente, fornecendo uma mensagem contextual para o usuário. Você também deve usar indicadores de progresso para fornecer comentários aos usuários sobre processos de execução longa.

## <a name="testing-on-mobile-clients"></a>Teste em clientes móveis

Você deve validar se a guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para Android dispositivos, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela está em execução. É recomendável que você teste em dispositivos de alto e baixo desempenho, incluindo um tablet.

## <a name="distribution"></a>Distribuição

Os aplicativos listados na Teams devem ser aprovados para uso móvel para funcionar corretamente no Teams cliente móvel. A disponibilidade e o comportamento da guia dependem da aprovação do aplicativo.

### <a name="apps-on-teams-store-approved-for-mobile"></a>Aplicativos Teams store aprovados para dispositivos móveis

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo é listado na Teams e aprovado para uso móvel:

|Recursos   |Disponibilidade móvel?   |Comportamento móvel|
|----------|-----------|------------|
|Canal <br /> e guia grupo|Sim|A guia é aberta Teams cliente móvel usando a configuração do `contentUrl` aplicativo.|
|Aplicativo pessoal|Sim|Cada guia na guia do aplicativo pessoal é aberta no Teams móvel usando sua respectiva configuração`contentUrl`.|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Aplicativos Teams store não aprovados para dispositivos móveis

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo é listado na Teams, mas não é aprovado para uso móvel:

| Recursos | Disponibilidade móvel? | Comportamento móvel |
|----------|-----------|------------|
|Guia Canal e grupo|Sim|A guia é aberta no navegador padrão do dispositivo em vez do cliente Teams móvel `websiteUrl` usando a configuração do aplicativo, `setSettings()` que também deve ser incluída na função do [código-fonte](/microsoftteams/platform/tabs/how-to/using-teams-client-sdk#settings-namespace). No entanto, os usuários podem exibir a guia Teams cliente móvel selecionando Mais ao  lado do aplicativo e escolhendo **Abrir**, o que dispara a configuração do aplicativo`contentUrl`.|
|Aplicativo pessoal|Não|Não aplicável|

### <a name="apps-not-on-teams-store"></a>Aplicativos que não Teams loja

Se você estiver recarregando seu aplicativo ou publicando no catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo que Teams aplicativos da loja aprovados pela Microsoft para dispositivos móveis.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obtenha contexto para sua guia](~/tabs/how-to/access-teams-context.md)

## <a name="see-also"></a>Confira também

* [Diretrizes de design de guia](~/tabs/design/tabs.md)
* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Planejar o Teams mobile – Teams](~/concepts/design/plan-responsive-tabs-for-teams-mobile.md)
