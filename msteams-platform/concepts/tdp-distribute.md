---
title: Distribuir seus aplicativos
description: Saiba como distribuir seus aplicativos usando o Portal do Desenvolvedor para Microsoft Teams.
keywords: iniciando equipes do portal do desenvolvedor
localization_priority: Normal
ms.topic: Conceptual
ms.openlocfilehash: d1d098b295492a7dc3b691db4625307b6c3170ce
ms.sourcegitcommit: 25539046d408c4270b988fd826d7cf1275f4b9dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52763123"
---
# <a name="distribute-your-apps"></a>Distribuir seus aplicativos

## <a name="distribute"></a>Distribuir

Depois de terminar de definir seu aplicativo, a seção **Distribuir** permite exportar a definição do aplicativo como um arquivo zip que, em seguida, pode ser compartilhado e carregado no cliente Teams para teste. Clicar em exportar baixa o arquivo zip como **appname.zip** no seu diretório de download padrão.

:::image type="content" source="~/assets/images/tdp/tdp_distribute_1.png" alt-text="Captura de tela mostrando a página Distribuir do Teams Portal do Desenvolvedor.":::

### <a name="manifest"></a>Manifesto

O manifesto descreve como seu aplicativo é configurado, incluindo seus recursos, recursos necessários e outros atributos importantes. Consulte [esquema de manifesto](~/resources/schema/manifest-schema.md) para obter mais informações.

### <a name="flights"></a>Flights

Controle quem recebe atualizações de aplicativos. Por exemplo, você pode liberar uma atualização para os funcionários da Microsoft para identificar e corrigir bugs antes de liberá-lo para o público. Selecione **Criar uma Nova Solicitação** para criar uma nova solicitação de voo.

### <a name="publish-to-org"></a>Publicar na organização

Disponibilizar seu aplicativo para as pessoas em sua organização. Depois de aprovado pelo administrador de IT, seu aplicativo será apresentado no Teams em Aplicativos > Criado para sua organização.

### <a name="publish-your-app-to-teams-store"></a>Publicar seu aplicativo no Teams store

Na página inicial do seu projeto, você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da empresa para os usuários em sua organização ou enviar seu aplicativo para a Fonte de Aplicativos para todos os usuários do Teams. Seu administrador de TI revisará esses envios. Você pode retornar à página **Publicar** para verificar o status do envio e saber se o aplicativo foi aprovado ou rejeitado pelo administrador de TI. Esse também é o local onde você deverá enviar atualizações para o aplicativo ou cancelar os envios ativos no momento.

## <a name="see-also"></a>Confira também

* [Visão geral do Teams Portal do Desenvolvedor](~/concepts/build-and-test/teams-developer-portal.md)
* [Configurar Teams Portal do Desenvolvedor](~/concepts/tdp-configuration.md)
* [Ferramentas no Teams Portal do Desenvolvedor](~/concepts/tdp-tools.md)