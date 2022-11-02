---
title: Guias em dispositivos móveis
description: Saiba como a guia funciona em clientes Android e iOS Microsoft Teams (móveis), sua autenticação, conexão de baixa largura de banda, teste ou distribuição.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: 8dac56cd609466c116f39baf5dc9d9a7970645ec
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820077"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

Ao criar um aplicativo do Microsoft Teams que inclua uma guia, você deve testar como sua guia funciona nos clientes Do Microsoft Teams android e iOS. Este artigo descreve alguns dos principais cenários que você deve considerar.

Se você optar por fazer com que a guia canal ou grupo apareça em clientes móveis do Teams, a [`setSettings()`](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-settings-setsettings&preserve-view=true) configuração deverá ter um valor para a `websiteUrl` propriedade. Para garantir a experiência ideal do usuário, você deve seguir as diretrizes para guias no celular neste artigo ao criar suas guias.

Os aplicativos [distribuídos pela loja do Teams](~/concepts/deploy-and-publish/appsource/publish.md) têm um processo de aprovação separado para clientes móveis. O comportamento padrão desses aplicativos é o seguinte:

| **Funcionalidade do aplicativo** | **Comportamento se o aplicativo for aprovado** | **Comportamento se o aplicativo não for aprovado** |
| --- | --- | --- |
| **Guias pessoais** | O aplicativo aparece na barra inferior dos clientes móveis. As guias são abertas no cliente do Teams. | O aplicativo não aparece na barra inferior dos clientes móveis. |
| **Guias de canal e grupo** | A guia é aberta no cliente do Teams usando `contentUrl`. | A guia é aberta em um navegador fora do cliente do Teams usando `websiteUrl`. |

> [!NOTE]
>
> * Os aplicativos enviados ao [AppSource](https://appsource.microsoft.com) para publicação no Teams são avaliados automaticamente para capacidade de resposta móvel. Para consultas, entre em contato com teamsubm@microsoft.com.
> * Para todos os aplicativos que não são distribuídos por meio do AppSource, as guias abrem em uma webview no aplicativo dentro dos clientes do Teams por padrão e não há nenhum processo de aprovação separado necessário.
> * O comportamento padrão dos aplicativos só é aplicável se distribuído pela loja do Teams. Por padrão, todas as guias são abertas no cliente do Teams.
> * Para iniciar uma avaliação do aplicativo para a simpatia móvel, entre em contato com teamsubm@microsoft.com com os detalhes do aplicativo.

## <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK do Teams JavaScript para pelo menos a versão 1.4.1.

## <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Os clientes móveis funcionam com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com qualquer tempo limite adequadamente fornecendo uma mensagem contextual para o usuário. Você também deve usar indicadores de progresso para fornecer comentários aos seus usuários para quaisquer processos de execução longa.

## <a name="testing-on-mobile-clients"></a>Teste em clientes móveis

Você deve validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar [DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela está em execução. É recomendável testar em dispositivos de alto e baixo desempenho, incluindo um tablet.

## <a name="distribution"></a>Distribuição

Os aplicativos listados na loja do Teams devem ser aprovados para uso móvel para funcionar corretamente no cliente móvel do Teams. A disponibilidade e o comportamento da guia dependem da aprovação do aplicativo.

### <a name="apps-on-teams-store-approved-for-mobile"></a>Aplicativos na loja do Teams aprovados para dispositivos móveis

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo é listado na loja do Teams e aprovado para uso móvel:

|Recursos   |Disponibilidade móvel?   |Comportamento móvel|
|----------|-----------|------------|
|Canal <br /> e guia grupo|Sim|A guia é aberta no cliente móvel do Teams usando a configuração do `contentUrl` seu aplicativo.|
|Aplicativo pessoal|Sim|Cada guia na guia aplicativo pessoal é aberta no cliente móvel do Teams usando sua respectiva `contentUrl` configuração.|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Aplicativos na loja do Teams não aprovados para dispositivos móveis

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo está listado na loja do Teams, mas não aprovado para uso móvel:

| Recursos | Disponibilidade móvel? | Comportamento móvel |
|----------|-----------|------------|
|Guia Canal e grupo|Sim|A guia é aberta no navegador padrão do dispositivo em vez do cliente móvel do Teams usando a configuração do `websiteUrl` aplicativo, que também deve ser incluída na [função](/microsoftteams/platform/tabs/how-to/using-teams-client-sdk#settings-namespace) do `setSettings()` código-fonte. No entanto, os usuários podem exibir a guia no cliente móvel do Teams selecionando **Mais** ao lado do aplicativo e escolhendo **Abrir**, o que dispara a configuração do `contentUrl` seu aplicativo.|
|Aplicativo pessoal|Não|Não aplicável|

> [!NOTE]
> As mensagens de bot serão mostradas na seção chat se um aplicativo móvel tiver os recursos do bot e da guia.
>
> Ao selecionar **Chat** do aplicativo bot e selecionar **Mais (...)**, você não poderá ver a funcionalidade de guia desse aplicativo na lista. No entanto, se você selecionar **Mais (...)** no canto inferior direito da seção **Chat** , poderá exibir o aplicativo de guia com um link para a funcionalidade do aplicativo bot desse aplicativo.

### <a name="apps-not-on-teams-store"></a>Aplicativos que não estão na loja do Teams

Se você estiver carregando seu aplicativo ou publicando no catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo que os aplicativos de armazenamento do Teams aprovados pela Microsoft para dispositivos móveis.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obtenha contexto para sua guia](~/tabs/how-to/access-teams-context.md)

## <a name="see-also"></a>Confira também

* [Compilar guias para o Teams](../what-are-tabs.md)
* [Criar guias com Cartões Adaptáveis](../how-to/build-adaptive-card-tabs.md)
* [Criar uma guia pessoal](../how-to/create-personal-tab.md)
* [Planejar guias responsivas para o aplicativo móvel do Teams](../../concepts/design/plan-responsive-tabs-for-teams-mobile.md)
* [Projete sua guia para o Microsoft Teams](tabs.md)
* [Guias do DevTools para o Microsoft Teams](../how-to/developer-tools.md)
* [Testar seu aplicativo](../../concepts/build-and-test/test-app-overview.md)
* [Distribuir seu aplicativo Microsoft Teams](../../concepts/deploy-and-publish/apps-publish-overview.md)
* [Criar pacote de aplicativos do Teams](../../concepts/build-and-test/apps-package.md)
