---
title: Visão geral do Live Share
author: surbhigupta
description: Neste módulo, saiba o que é o SDK do Microsoft Live Share e seus cenários de usuário.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 3738ee1037c87f283fd31ebdaba53b57f1784bb2
ms.sourcegitcommit: 134ce9381891e51e6327f1f611fdfd60c90cca18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2022
ms.locfileid: "67425621"
---
---

# <a name="live-share-sdk"></a>SDK do Live Share

> [!NOTE]
> No momento, o SDK do Live Share está disponível na [Versão Prévia do Desenvolvedor Público](../resources/dev-preview/developer-preview-intro.md). Você deve fazer parte da Versão Prévia do Desenvolvedor Público do Microsoft Teams para usar o Live Share.

O Live Share é um SDK projetado para transformar aplicativos do Teams em experiências colaborativas de vários usuários sem escrever nenhum código de back-end dedicado. O Live Share integra perfeitamente as reuniões com [o Fluid Framework](https://fluidframework.com/). Fluid Framework é uma coleção de bibliotecas de cliente para distribuir e sincronizar o estado compartilhado. Live Share fornece uma versão gratuita, totalmente gerenciada e pronta para usar o [Azure Fluid Relay](/azure/azure-fluid-relay/) suportado pela segurança e escala global do Teams.

> [!div class="nextstepaction"]
> [Introdução](teams-live-share-quick-start.md)

O Live Share inclui uma `TeamsFluidClient` classe para se conectar a um Contêiner Fluido especial associado a cada reunião em algumas linhas de código. Além das estruturas de dados fornecidas pelo Fluid Framework, o Live Share também dá suporte a um novo conjunto de classes de estrutura de dados distribuídos (DDS) para simplificar a criação de aplicativos para cenários comuns de reunião, como reprodução de mídia compartilhada.

:::image type="content" source="../assets/images/teams-live-share/teams-live-share-contoso-video.gif" alt-text="Experiência de compartilhamento de vídeo do Live Share":::

## <a name="why-build-apps-with-live-share"></a>Por que criar aplicativos com o Live Share?

Criar aplicativos colaborativos pode ser difícil, demorado, caro e inclui requisitos complexos de conformidade em escala. Os usuários do Teams passam um tempo significativo revisando o trabalho com colegas de equipe, assistindo vídeos juntos e debatendo novas ideias através do compartilhamento de telas. O SDK do Live Share permite transformar seu aplicativo em algo mais colaborativo com o mínimo de investimento.

Aqui estão alguns dos principais benefícios do SDK do Live Share:

- Gerenciamento e segurança de sessão sem complicações.
- Estruturas de dados distribuídos com e sem estado.
- Extensões de mídia para sincronizar facilmente vídeo e áudio.
- Respeitar os privilégios de reunião usando a verificação de função.
- Serviço gratuito e totalmente gerenciado com baixa latência.
- Atenuação automática de áudio inteligente.

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-schematics.png" alt-text="Teams Live Share":::

Para entender se o Live Share é ideal para seu cenário colaborativo, é útil entender as diferenças entre o Live Share e outras estruturas colaborativas, incluindo:

- [Soquetes da Web](#web-sockets)
- [Azure Fluid Relay](#azure-fluid-relay)
- [Live Share](#live-share-hosted-service)

### <a name="web-sockets"></a>Soquetes da Web

Os soquetes da Web são uma tecnologia onipresente para comunicação em tempo real na Web, e alguns aplicativos podem preferir usar seu próprio back-end de soquete da Web personalizado. Ao contrário das APIs REST, os soquetes da Web mantêm uma conexão aberta entre um servidor e clientes em uma sessão.

Assim como outros serviços de API personalizados, os requisitos normalmente incluem autenticação de sessões, mapeamento regional, manutenção e escala. Muitos cenários colaborativos também exigem a manutenção do estado da sessão no servidor, o que requer infraestrutura de armazenamento, resoluções de conflitos e muito mais.

### <a name="azure-fluid-relay"></a>Azure Fluid Relay

[O Azure Fluid Relay](/azure/azure-fluid-relay/) é uma oferta gerenciada para o Fluid Framework que ajuda os desenvolvedores a criar experiências colaborativas em tempo real e replicar o estado entre clientes JavaScript conectados. O Microsoft Whiteboard, o Loop e o OneNote são exemplos de aplicativos criados com o Fluid Framework atualmente.

Assim como outros serviços do Azure, o Azure Fluid Relay foi projetado para se adaptar às suas necessidades individuais de projeto com complexidade mínima. Os requisitos incluem o desenvolvimento de uma história de autenticação para seus contêineres fluid e conformidade regional. Depois de configurados, os desenvolvedores podem se concentrar em fornecer experiências colaborativas de alta qualidade.

### <a name="live-share-hosted-service"></a>Serviço hospedado do Live Share

O Live Share fornece um serviço turn-key do Azure Fluid Relay apoiado pela segurança das reuniões do Microsoft Teams. Os contêineres do Live Share são restritos aos participantes da reunião, mantêm os requisitos de residência de locatário e podem ser acessados em algumas linhas de código do cliente.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { TeamsFluidClient, EphemeralPresence } from "@microsoft/live-share";

// Join the Fluid container
const client = new TeamsFluidClient();
const schema = {
  initialObjects: { presence: EphemeralPresence },
};
const { container } = await client.joinContainer(schema);

// ... ready to start app sync logic
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { TeamsFluidClient, EphemeralPresence } from "@microsoft/live-share";
import { ContainerSchema } from "fluid-framework";

// Join the Fluid container
const client = new TeamsFluidClient();
const schema: ContainerSchema = {
  initialObjects: { presence: EphemeralPresence },
};
const { container } = await client.joinContainer(schema);

// ... ready to start app sync logic
```

---

> [!IMPORTANT]
> Todos os dados enviados ou armazenados por meio do serviço hospedado do Azure Fluid Relay do SDK do Live Share podem ser acessados por até 24 horas. Para obter mais informações, [consulte as perguntas frequentes do Live Share](teams-live-share-faq.md).

#### <a name="using-a-custom-azure-fluid-relay-service"></a>Usando um serviço personalizado do Azure Fluid Relay

Embora a maioria de vocês ache preferível usar nosso serviço hospedado gratuito, ainda há situações em que é útil usar seu próprio serviço do Azure Fluid Relay para seu aplicativo Live Share.

Considere usar um serviço personalizado se você:

- Exigir o armazenamento de dados em contêineres Fluid além do tempo de vida de uma reunião.
- Transmita dados confidenciais por meio do serviço que requer uma política de segurança personalizada.
- Desenvolva recursos por meio do Fluid Framework, por exemplo, `SharedMap`para seu aplicativo fora do Teams.

Para obter mais informações, consulte o guia de instruções personalizado do serviço do Azure Fluid [Relay.](./teams-live-share-how-to/how-to-custom-azure-fluid-relay.md)

## <a name="user-scenarios"></a>Cenários de usuário

| Cenário                                                                                | Exemplo                                                                                                                                                                                            |
| :-------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Durante uma revisão de marketing, um usuário deseja coletar comentários sobre sua edição de vídeo mais recente. | O usuário compartilha o vídeo para o estágio de reunião e inicia o vídeo. Conforme necessário, o usuário pausa o vídeo para discutir a cena e os participantes desenham partes da tela para enfatizar os pontos-chave. |
| Um gerente de projeto joga Agile Poker com sua equipe durante o planejamento.                    | O gerente compartilha um aplicativo Agile Poker para o estágio de reunião que permite jogar o jogo de planejamento até que a equipe tenha consenso.                                                                        |
| Um consultor financeiro revisa documentos PDF com clientes antes de assinar.                  | O consultor financeiro compartilha o contrato pdf para o estágio da reunião. Todos os participantes podem ver cursores e texto realçado no PDF, após o qual ambas as partes assinarão o contrato.        |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Introdução](teams-live-share-quick-start.md)

## <a name="see-also"></a>Confira também

- [Repositório do GitHub](https://github.com/microsoft/live-share-sdk)
- [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
- [Documentos de referência do SDK do Live Share Media](/javascript/api/@microsoft/live-share-media/)
- [Recursos do Live Share ](teams-live-share-capabilities.md)
- [Funcionalidades de mídia do Live Share](teams-live-share-media-capabilities.md)
- [Perguntas frequentes do Live Share](teams-live-share-faq.md)
- [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
