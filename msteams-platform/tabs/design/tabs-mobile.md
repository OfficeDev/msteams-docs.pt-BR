---
title: Guias em dispositivos móveis
description: Saiba como a guia funciona em clientes Android e iOS do Microsoft Teams (móvel), sua autenticação, conexão de baixa largura de banda, teste ou distribuição.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: 0dbb74d5c2854897f82708aa83a0c49df4f28890
ms.sourcegitcommit: bd96080c78f25eb0a67ce176df5e255be348f7b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2022
ms.locfileid: "68575765"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

Ao criar um aplicativo do Microsoft Teams que inclui uma guia, você deve testar como sua guia funciona nos clientes Android e iOS do Microsoft Teams. Este artigo descreve alguns dos principais cenários que você deve considerar.

Se você optar por exibir seu canal ou guia de grupo em clientes móveis do Teams, [`setSettings()`](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-settings-setsettings&preserve-view=true) a configuração deverá ter um valor para a `websiteUrl` propriedade. Para garantir a experiência ideal do usuário, você deve seguir as diretrizes para guias sobre dispositivos móveis neste artigo ao criar suas guias.

Os [aplicativos distribuídos por meio da loja do Teams](~/concepts/deploy-and-publish/appsource/publish.md) têm um processo de aprovação separado para clientes móveis. O comportamento padrão desses aplicativos é o seguinte:

| **Funcionalidade do aplicativo** | **Comportamento se o aplicativo for aprovado** | **Comportamento se o aplicativo não for aprovado** |
| --- | --- | --- |
| **Guias pessoais** | O aplicativo aparece na barra inferior dos clientes móveis. As guias são abertas no cliente do Teams. | O aplicativo não aparece na barra inferior dos clientes móveis. |
| **Guias de canal e grupo** | A guia é aberta no cliente do Teams usando `contentUrl`. | A guia é aberta em um navegador fora do cliente do Teams usando `websiteUrl`. |

> [!NOTE]
>
> * Os aplicativos enviados ao [AppSource](https://appsource.microsoft.com) para publicação no Teams são avaliados automaticamente quanto à capacidade de resposta móvel. Para qualquer consulta, entre em contato com teamsubm@microsoft.com.
> * Para todos os aplicativos que não são distribuídos por meio do AppSource, as guias são abertas em um modo de exibição da Web no aplicativo dentro dos clientes do Teams por padrão e não há nenhum processo de aprovação separado necessário.
> * O comportamento padrão dos aplicativos só será aplicável se for distribuído por meio da loja do Teams. Por padrão, todas as guias são abertas no cliente do Teams.
> * Para iniciar uma avaliação do seu aplicativo para fins de amizade móvel, entre em contato com teamsubm@microsoft.com com os detalhes do aplicativo.

## <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK javaScript do Teams para pelo menos a versão 1.4.1.

## <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Os clientes móveis funcionam com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com os tempos limite adequadamente, fornecendo uma mensagem contextual para o usuário. Você também deve usar indicadores de progresso para fornecer comentários aos usuários sobre processos de execução longa.

## <a name="testing-on-mobile-clients"></a>Teste em clientes móveis

Você deve validar se a guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela está em execução. É recomendável que você teste em dispositivos de alto e baixo desempenho, incluindo um tablet.

## <a name="distribution"></a>Distribuição

Os aplicativos listados na loja do Teams devem ser aprovados para uso móvel para funcionar corretamente no cliente móvel do Teams. A disponibilidade e o comportamento da guia dependem da aprovação do aplicativo.

### <a name="apps-on-teams-store-approved-for-mobile"></a>Aplicativos na loja do Teams aprovados para dispositivos móveis

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo é listado na loja do Teams e aprovado para uso móvel:

|Recursos   |Disponibilidade móvel?   |Comportamento móvel|
|----------|-----------|------------|
|Canal <br /> e guia grupo|Sim|A guia é aberta no cliente móvel do Teams usando a configuração do `contentUrl` aplicativo.|
|Aplicativo pessoal|Sim|Cada guia na guia do aplicativo pessoal é aberta no cliente móvel do Teams usando sua respectiva configuração `contentUrl` .|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Aplicativos na loja do Teams não aprovados para dispositivos móveis

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo é listado na loja do Teams, mas não é aprovado para uso móvel:

| Recursos | Disponibilidade móvel? | Comportamento móvel |
|----------|-----------|------------|
|Guia Canal e grupo|Sim|A guia é aberta no navegador padrão do dispositivo em vez do cliente móvel do Teams `websiteUrl` usando a configuração do aplicativo, que também deve ser incluída na função do [código-fonte](/microsoftteams/platform/tabs/how-to/using-teams-client-sdk#settings-namespace)`setSettings()`. No entanto, os usuários podem exibir a guia no cliente móvel do  Teams selecionando Mais ao lado do aplicativo e escolhendo **Abrir**, o que dispara a configuração do aplicativo`contentUrl`.|
|Aplicativo pessoal|Não|Não aplicável|

> [!NOTE]
> As mensagens do bot serão mostradas na seção de chat se um aplicativo móvel tiver os recursos de bot e guia.
>
> Ao selecionar **o Chat** do aplicativo de bot e selecionar **Mais (...),** você não poderá ver a funcionalidade de guia desse aplicativo na lista. No entanto, se você selecionar **Mais (...)** no canto inferior direito da seção **Chat** , poderá exibir o aplicativo de guia com um link para a funcionalidade do aplicativo de bot desse aplicativo.

### <a name="apps-not-on-teams-store"></a>Aplicativos que não estão na loja do Teams

Se você estiver recarregando seu aplicativo ou publicando no catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo que os aplicativos da loja do Teams aprovados pela Microsoft para dispositivos móveis.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obtenha contexto para sua guia](~/tabs/how-to/access-teams-context.md)

## <a name="see-also"></a>Confira também

* [Diretrizes de design de guia](~/tabs/design/tabs.md)
* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Planejar o teams mobile - Teams](~/concepts/design/plan-responsive-tabs-for-teams-mobile.md)
