---
title: Visão geral do Live Share
description: Neste módulo, saiba o que é o SDK do Microsoft Live Share e seus cenários de usuário.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.openlocfilehash: 5fa509ee7835db80a99487ed7d42ab7d6ed8341d
ms.sourcegitcommit: 09ee0305b827ad6d1368d892db3824c5dbad886f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65759652"
---
---

# <a name="live-share-sdk"></a>SDK do Live Share

> [!Note]
> O SDK do Live Share está disponível atualmente apenas na [Versão Prévia do Desenvolvedor Público](../resources/dev-preview/developer-preview-intro.md). Você precisa fazer parte da Versão Prévia do Desenvolvedor Público do Microsoft Teams para usar o SDK do Live Share.

O Live Share é um SDK projetado para transformar aplicativos do Teams em experiências colaborativas de vários usuários sem escrever nenhum código de back-end dedicado. O SDK do Live Share integra perfeitamente as reuniões ao [Fluid Framework](https://fluidframework.com/). Fluid Framework é uma coleção de bibliotecas de cliente para distribuir e sincronizar o estado compartilhado. Live Share fornece uma versão gratuita, totalmente gerenciada e pronta para usar o [Azure Fluid Relay](/azure/azure-fluid-relay/) suportado pela segurança e escala global do Teams.

> [!div class="nextstepaction"]
> [Introdução](teams-live-share-quick-start.md)

O SDK do Live Share `TeamsFluidClient` fornece uma classe para conexão a um Contêiner Fluido especial associado a cada reunião em algumas linhas de código. Além das estruturas de dados fornecidas pelo Fluid Framework, o Live Share também dá suporte a um novo conjunto de classes de estrutura de dados distribuídos (DDS) para simplificar a criação de aplicativos para cenários comuns de reunião, como reprodução de mídia compartilhada.

:::image type="content" source="../assets/images/teams-live-share/teams-live-share-contoso-video.gif" alt-text="Experiência de compartilhamento de vídeo do Live Share":::

## <a name="why-build-apps-using-the-live-share-sdk"></a>Por que criar aplicativos usando o SDK do Live Share?

Criar aplicativos colaborativos pode ser difícil, demorado, caro e inclui requisitos complexos de conformidade em escala. Os usuários do Teams passam um tempo significativo revisando o trabalho com colegas de equipe, assistindo vídeos juntos e debatendo novas ideias através do compartilhamento de telas. O SDK do Live Share permite transformar seu aplicativo em algo mais colaborativo com o mínimo de investimento.

Aqui estão alguns dos principais benefícios do SDK do Live Share:

* Gerenciamento e segurança de sessão sem complicações
* Estruturas de dados distribuídos com e sem estado
* Extensões de mídia para sincronizar facilmente vídeo e áudio
* Respeitar os privilégios de reunião usando a verificação de função
* Serviço gratuito e totalmente gerenciado com baixa latência
* Atenuação automática de áudio inteligente

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-schematics.png" alt-text="Teams Live Share":::

## <a name="user-scenarios"></a>Cenários de usuário

|Cenário|Exemplo|
| :------- | :--------------------- |
| Os usuários e seus colegas de trabalho agendaram uma reunião para apresentar uma edição antecipada de um vídeo de marketing em uma próxima análise de liderança e querem destacar seções específicas para comentários. | Os usuários compartilham o vídeo na janela de conteúdo compartilhado na reunião e iniciam o vídeo. Conforme necessário, o usuário pausa o vídeo para discutir a cena. Os usuários podem se revezar desenhando partes da tela para enfatizar os principais pontos.|
| Você é um gerente de projetos de uma equipe ágil que joga Agile Poker com sua equipe para estimar a quantidade de trabalho necessária para uma iteração futura.| Você compartilha um aplicativo de planejamento do Agile Poker na janela de conteúdo compartilhado na reunião que usa o SDK do Live Share e joga o jogo de planejamento até que a equipe chegue a um consenso.|

> [!IMPORTANT]
> Todos os dados enviados ou armazenados por meio do serviço Azure Fluid Relay hospedado pelo SDK do Live Share ficam acessíveis por 24 horas. Para obter mais informações, [consulte as perguntas frequentes do Live Share](teams-live-share-faq.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Introdução](teams-live-share-quick-start.md)

## <a name="see-also"></a>Confira também

* [Repositório do GitHub](https://github.com/microsoft/live-share-sdk)
* [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
* [Documentos de referência do SDK do Live Share Media](/javascript/api/@microsoft/live-share-media/)
* [Recursos do Live Share ](teams-live-share-capabilities.md)
* [Funcionalidades de mídia do Live Share](teams-live-share-media-capabilities.md)
* [Perguntas frequentes do Live Share](teams-live-share-faq.md)
* [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
