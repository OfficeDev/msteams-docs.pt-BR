---
title: Planejar a visão geral do seu aplicativo
author: heath-hamilton
description: Entenda o caso de uso e os recursos do aplicativo Microsoft Teams, mapeie casos de uso, planeje guias responsivas para dispositivos móveis. Conheça os recursos e a disponibilidade do Teams para GCC, GCC-High e DOD.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: lajanuar
ms.openlocfilehash: eb72d4296ee6b91bae1775ad79eef06139abb59e
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100417"
---
# <a name="plan-your-app-with-teams-features"></a>Planeje seu aplicativo com os recursos do Microsoft Teams

Criar um aplicativo incrível do Teams tem tudo a ver com encontrar a combinação certa de recursos para atender às necessidades do usuário. O design, os recursos e funcionalidades de um aplicativo derivam dessa finalidade.

At its heart, Teams is a collaboration platform. It's also a social platform, is natively cross-platform, sits at the heart of Office 365, and offers a personal canvas for you to create apps.

Nesta seção, saiba como:

* Identifique e mapeie casos de uso para recursos do Microsoft Teams.
* Utilize a lista de verificação de planejamento.
* Planeje além da Implantação de aplicativos.

## <a name="plan-with-teams"></a>Planejar com Microsoft Teams

O Microsoft Teams como plataforma oferece kits de ferramentas, bibliotecas e aplicativos em todos os estágios do desenvolvimento de aplicativos. Vamos dividi-lo para o ciclo de vida de criação de aplicativos:

:::image type="content" source="../assets/images/app-fundamentals/plan-app.png" alt-text="A ilustração mostra o planejamento do seu aplicativo":::

* [Antes da sua build](#before-you-build)
* [Durante a build](#during-build)
* [Pós-build](#post-build)
* [Lista de verificação de planejamento](../concepts/design/planning-checklist.md)

### <a name="before-you-build"></a>Antes da sua build

Entender o usuário e sua preocupação são os primeiros indicadores de como um aplicativo do Microsoft Teams pode ajudar. Construa seu caso de uso em torno do problema, determine como um aplicativo pode resolvê-lo e desenhe uma solução.

* **Entenda seu caso de uso e os recursos do Aplicativo Teams**: Entenda os requisitos do seu usuário e você poderá identificar os recursos certos.

* **Mapear seus casos de uso**: Mapeie casos de uso comuns para recursos do Teams com base em requisitos, tais como compartilhamento, colaboração, fluxos de trabalho, plataformas sociais relevantes e muito mais.

* **Planeje guias responsivas para o Microsoft Teams Mobile**: Ele aborda cenários comuns e ajuda no planejamento de aplicativos para o Teams Mobile.

### <a name="during-build"></a>Durante a build

* **Criar e Compilar projeto de aplicativos**: Com o Microsoft Teams, você pode escolher o ambiente de compilação que melhor se adapta aos seus requisitos de aplicativo. Use o Kit de Ferramentas do Teams ou outros SDKs, como C#, Blazor, Node.js e muito mais para começar.

* **Crie a interface do usuário do seu aplicativo**: use o Teams UI Toolkit e a UI Library para projetar o layout do seu aplicativo.

* **Use o Microsoft Teams como uma plataforma**: A plataforma do Microsoft Teams ajuda você a criar um aplicativo único ou com vários recursos. Seu aplicativo Teams é suportado por produtos e serviços integrados que fortalecem a experiência do aplicativo.

    :::image type="content" source="../assets/images/overview/teams-solution.png" alt-text="Representação conceitual da solução do Microsoft Teams.":::

    Seus aplicativos aparecem no Teams como guias, bots, extensões de mensagens, conectores e webhooks ou como um aplicativo de vários recursos. Essas funcionalidades são habilitadas no back-end pelos aplicativos Azure, Microsoft Graph, SharePoint e Power que ajudam a automatizar tarefas e processos.

    Juntos, essas funcionalidades dão vida à sua solução de aplicativo.

* **Integrar funcionalidades do dispositivo**: Você pode integrar as funcionalidades nativos do dispositivo em seu aplicativo, tais como câmera, leitor de QR ou código de verificador, galeria de fotos, microfone e localização.

### <a name="post-build"></a>Pós-build

* Integre seu aplicativo com o Teams e outros aplicativos, tais como o Microsoft 365, Microsoft Graph e muito mais.
* Utilize o Portal do Desenvolvedor para configurar, gerenciar e implantar seu aplicativo.

### <a name="government-community-cloud"></a>Nuvem da Comunidade Governamental

Nuvem da Comunidade Governamental (GCC) é uma cópia do ambiente comercial focada no governo. O Departamento de Defesa (DOD) e os prestadores de serviço federais devem atender aos rigorosos requisitos de segurança cibernética e conformidade. Para esse fim, a GCC-High foi criada para atender às necessidades dos prestadores de serviços Federais e do DOD. A GCC-High é uma cópia da nuvem do DOD, mas existe em seu próprio ambiente soberano. A nuvem do DOD foi criada somente para o Departamento de Defesa.

A tabela a seguir inclui os recursos e a disponibilidade do Teams para a GCC, GCC-High e o DOD:

| Recursos   | CCG | GCC-High | DOD |
|-------------|---------|---|---|
| Aplicativos de propriedade de Teams como em aplicativos desenvolvidos internamente | ✔️ O aplicativo está habilitado se tiverGCC | ✔️ O aplicativo está habilitado se tiver GCC-High | ✔️ O aplicativo está habilitado se tiver DOD |
| Aplicativos da Microsoft | ✔️ Aplicativos da Microsoft compatíveis com o GCC | ✔️ Aplicativos da Microsoft compatíveis com a GCC-High. | ✔️ Aplicativos da Microsoft compatíveis com o DOD |
| Aplicativos 3P ou de terceiros | ✔️ Third-party apps are available. Disabled by default and tenant admin use their own discretion to enable it. | ❌ | ❌ |
| Bots | ✔️ | ❌ | ❌ |
| Aplicativos de guia personalizados ou Lob |  ✔️ | ✔️ | ✔️ |
| Sideload de aplicativos | ✔️ | ❌ | ❌ |
| Bots personalizados ou Lob | ✔️ | ❌ | ❌ |
| Extensões de mensagens personalizadas | ❌ | ❌ | ❌ |
| Conectores personalizados | ❌ | ❌ | ❌ |

**Conformidade da Interface do Usuário**: Ao habilitar as comunicações de terceiros, os clientes aceitam que tal comunicação esteja sendo processada por terceiros e não pela Microsoft. O cliente é o único responsável por mitigar os riscos associados à conexão com bots de terceiros em seus serviços. A Microsoft não endossa e não oferece garantias, expressas ou implícitas, em relação à segurança de terceiros que o cliente permite que se conectem ao seu serviço. Habilitar os bots estenderá o limite do seu sistema além desse locatário com base no bot que você escolher para aproveitar. É sua responsabilidade garantir que isso atenda aos seus requisitos de conformidade, incluindo FedRAMP, DFARS, ITAR, etc. É sua responsabilidade avaliar o risco e a conformidade de qualquer ponto de extremidade e URL ao qual você se conectar.

A lista a seguir ajuda a identificar a disponibilidade da GCC, GCC High e do DOD para os recursos:

* Para aplicativos de terceiros, consulte [aplicativos Web](../samples/integrating-web-apps.md) e [extensibilidade de aplicativos de reunião](../apps-in-teams-meetings/meeting-app-extensibility.md).
* Para bots, consulte [criar seu primeiro bot de conversação para o Teams](../get-started/first-app-bot.md), [criação do seu bot do Teams](../bots/design/bots.md), [adicionar bots aos aplicativos do Microsoft Teams](../resources/bot-v3/bots-overview.md) e [bots no Teams](../bots/what-are-bots.md).
* Para aplicativos de sideload, consulte [permitir que seu aplicativo Microsoft Teams seja personalizado](../concepts/design/enable-app-customization.md), [distribuir seu aplicativo Microsoft Teams](../concepts/deploy-and-publish/apps-publish-overview.md) e [Carregar seu aplicativo no Teams ](../concepts/deploy-and-publish/apps-upload.md).
* Para conectores personalizados, consulte [criar conectores do Office 365 para Microsoft Teams](../webhooks-and-connectors/how-to/connectors-creating.md).

</details>

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Casos de uso e recursos do Microsoft Teams](design/understand-use-cases.md)

## <a name="see-also"></a>Confira também

* [Lista de verificação de planejamento](../concepts/design/planning-checklist.md)
* [Considerações para a integração do Microsoft Teams](../samples/integrating-web-apps.md)
* [Crie seu primeiro aplicativo do Microsoft Teams ](../build-your-first-app/build-first-app-overview.md)
