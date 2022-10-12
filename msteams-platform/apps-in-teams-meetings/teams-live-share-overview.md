---
title: Visão geral do Live Share
author: surbhigupta
description: Neste módulo, saiba o que é o SDK do Microsoft Live Share e seus cenários de usuário.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 38157dea1c2d24b82cf1f48829639fd1d92392c1
ms.sourcegitcommit: 0fa0bc081da05b2a241fd8054488d9fd0104e17b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68552522"
---
---

# <a name="live-share-sdk"></a>SDK do Live Share

> [!VIDEO https://www.youtube.com/embed/971YIvosuUk]

O Live Share é um SDK projetado para transformar aplicativos do Teams em experiências colaborativas de vários usuários sem escrever nenhum código de back-end dedicado. Com o Live Share, os usuários podem assistir, co-criar e co-editar durante as reuniões.

Às vezes, o compartilhamento de tela não é suficiente, e é por isso que a Microsoft criou ferramentas como o PowerPoint Live e o Whiteboard diretamente no Teams. Ao trazer seu aplicativo Web diretamente para o estágio central na interface de reunião, os usuários podem colaborar perfeitamente durante reuniões e chamadas.

> [!div class="nextstepaction"]
> [Introdução](teams-live-share-quick-start.md)

## <a name="feature-overview"></a>Visão geral dos recursos

O Live Share tem três pacotes que dão suporte a cenários colaborativos ilimitadas. Esses pacotes expõem um conjunto de DDS (estruturas de dados distribuídas), incluindo blocos de construção primitivos e cenários chave de turno.

O Live Share integra perfeitamente as reuniões com [o Fluid Framework](https://fluidframework.com/). Fluid Framework é uma coleção de bibliotecas de cliente para distribuir e sincronizar o estado compartilhado. Live Share fornece uma versão gratuita, totalmente gerenciada e pronta para usar o [Azure Fluid Relay](/azure/azure-fluid-relay/) suportado pela segurança e escala global do Teams.

### <a name="live-share-core"></a>Núcleo do Live Share

O Live Share permite conectar-se a um Contêiner Fluido especial associado a cada reunião em algumas linhas de código. Além das estruturas de dados fornecidas pelo Fluid Framework, o Live Share também dá suporte a um novo conjunto de classes DDS para simplificar a sincronização do estado do aplicativo em reuniões.

Os recursos compatíveis com o pacote principal do Live Share incluem:

- Ingresse na sessão do Live Share de uma reunião com `LiveShareClient`.
- Acompanhe a presença da reunião e sincronize os metadados do usuário com `LivePresence`.
- Envie eventos em tempo real para outros clientes na sessão com `LiveEvent`.
- Coordenar o estado do aplicativo que desaparece quando os usuários saem da sessão com `LiveState`.
- Sincronizar um temporizador de contagem regressiva com `LiveTimer`.
- Aproveite qualquer recurso do Fluid Framework, como `SharedMap` e `SharedString`.

Você pode encontrar mais informações sobre esse pacote na página [de recursos principais](./teams-live-share-capabilities.md).

### <a name="live-share-media"></a>Mídia do Live Share

:::image type="content" source="../assets/images/teams-live-share/teams-live-share-contoso-video.gif" alt-text="Experiência de compartilhamento de vídeo do Live Share":::

Vídeo e áudio são partes fundamentais do local de trabalho e do mundo modernos. A mídia do Live Share permite **a sincronização de mídia** para qualquer player de mídia com apenas algumas linhas de código. Ao sincronizar a mídia na camada de controles de transporte e estado do player, você pode atribuir exibições individualmente, fornecendo a melhor qualidade possível disponível por meio de seu aplicativo. Como a Microsoft não está readicastando seu conteúdo de mídia, seus requisitos de licenciamento e acesso são mantidos intactos.

Os recursos com suporte da mídia do Live Share incluem:

- Sincronize o estado do player de mídia e acompanhe com `MediaPlayerSynchronizer`.
- Ajustes inteligentes no volume de mídia à medida que os usuários falam durante a reunião.
- Limite quais usuários podem modificar o estado do player.
- Suspender e retomar a sincronização de mídia em tempo real ou em pontos de espera agendados.

Você pode encontrar mais informações sobre esse pacote na página [de mídia do Live Share](./teams-live-share-media-capabilities.md).

> [!NOTE]
> O Live Share não readicast conteúdo de mídia. Ele foi projetado para uso com web players inseridos, como HTML5 `<video>` ou Player de Mídia do Azure.

### <a name="live-share-canvas"></a>Tela do Live Share

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-schematics.png" alt-text="Teams Live Share":::

Ao colaborar em reuniões, é essencial que os usuários possam apontar e enfatizar o conteúdo na tela. A tela Live Share facilita a adição de escrita à tinta, apontadores laser e cursores ao seu aplicativo para uma colaboração perfeita.

Os recursos compatíveis com a tela do Live Share incluem:

- Adicione uma colaboração `<canvas>` ao seu aplicativo com `LiveCanvas`.
- Transmita ideias usando as ferramentas de caneta, realce, linha e seta.
- Apresente-se efetivamente usando o apontador laser.
- Acompanhe os cursores do mouse em tempo real.
- Defina as configurações para dispositivos variáveis e estados de exibição.
- Use entradas de mouse, toque e caneta totalmente compatíveis.

Você pode encontrar mais informações sobre esse pacote na página [de tela do Live Share](./teams-live-share-canvas.md).

## <a name="why-build-apps-with-live-share"></a>Por que criar aplicativos com o Live Share?

Criar aplicativos colaborativos pode ser difícil, demorado, caro e inclui requisitos complexos de conformidade em escala. Os usuários do Teams passam um tempo significativo revisando o trabalho com colegas de equipe, assistindo vídeos juntos e debatendo novas ideias através do compartilhamento de telas. O SDK do Live Share permite transformar seu aplicativo em algo mais colaborativo com o mínimo de investimento.

Aqui estão alguns dos principais benefícios do SDK do Live Share:

- Gerenciamento e segurança de sessão sem complicações.
- Estruturas de dados distribuídos com e sem estado.
- Extensões de mídia para sincronizar facilmente vídeo e áudio.
- Escrita à tinta de tecla de turno, apontadores laser e cursores.
- Respeitar os privilégios de reunião usando a verificação de função.
- Serviço gratuito e totalmente gerenciado com baixa latência.

Para entender se o Live Share é ideal para seu cenário colaborativo, é útil entender as diferenças entre o Live Share e outras estruturas colaborativas, incluindo:

- [Soquetes da Web](#web-sockets)
- [Azure Fluid Relay](#azure-fluid-relay)
- [Live Share](#live-share-hosted-service)

### <a name="web-sockets"></a>Soquetes da Web

Os soquetes da Web são uma tecnologia onipresente para comunicação em tempo real na Web, e alguns aplicativos podem preferir usar seu próprio back-end de soquete da Web personalizado. Ao contrário das APIs REST, os soquetes da Web mantêm uma conexão aberta entre um servidor e clientes em uma sessão.

Assim como outros serviços de API personalizados, os requisitos normalmente incluem autenticação de sessões, mapeamento regional, manutenção e escala. Muitos cenários colaborativos também exigem a manutenção do estado da sessão no servidor, o que requer infraestrutura de armazenamento, resoluções de conflitos e muito mais.

Ao usar o Live Share, você obtém todo o poder dos soquetes da Web sem nenhuma sobrecarga.

### <a name="azure-fluid-relay"></a>Azure Fluid Relay

[O Azure Fluid Relay](/azure/azure-fluid-relay/) é uma oferta gerenciada para o Fluid Framework que ajuda os desenvolvedores a criar experiências colaborativas em tempo real e replicar o estado entre clientes JavaScript conectados. O Microsoft Whiteboard, o Loop e o OneNote são exemplos de aplicativos criados com o Fluid Framework atualmente.

Assim como outros serviços do Azure, o Azure Fluid Relay foi projetado para se adaptar às suas necessidades individuais de projeto com complexidade mínima. Os requisitos incluem o desenvolvimento de uma história de autenticação para seus contêineres fluid e conformidade regional. Depois de configurados, os desenvolvedores podem se concentrar em fornecer experiências colaborativas de alta qualidade.

### <a name="live-share-hosted-service"></a>Serviço hospedado do Live Share

O Live Share fornece um serviço turn-key do Azure Fluid Relay apoiado pela segurança das reuniões do Microsoft Teams. Os contêineres do Live Share são restritos aos participantes da reunião, mantêm os requisitos de residência de locatário e podem ser acessados em algumas linhas de código do cliente.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient, LivePresence } from "@microsoft/live-share";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { presence: LivePresence },
};
const { container } = await liveShare.joinContainer(schema);

// ... ready to start app sync logic
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient, LivePresence } from "@microsoft/live-share";
import { ContainerSchema } from "fluid-framework";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema: ContainerSchema = {
  initialObjects: { presence: LivePresence },
};
const { container } = await liveShare.joinContainer(schema);

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

> [!IMPORTANT]
> O Live Share é licenciado sob a Licença do [SDK do Microsoft Live Share](https://github.com/microsoft/live-share-sdk/blob/main/LICENSE). Para usar esses recursos em seu aplicativo, primeiro você deve ler e concordar com esses termos.

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
