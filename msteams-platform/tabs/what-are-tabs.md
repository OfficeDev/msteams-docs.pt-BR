---
title: O que são guias personalizadas em Teams?
author: laujan
description: Uma visão geral das guias personalizadas na plataforma Teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 19c51d5c30f938dc5368b28b69ffeb29330887b4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566590"
---
# <a name="microsoft-teams-tabs"></a>Guias do Microsoft Teams

As guias são páginas da web Teams-aware incorporadas em Microsoft Teams. Eles são simples HTML <tags de iframe \> que apontam para domínios declarados no manifesto do aplicativo e podem ser adicionados como parte de um canal dentro de uma equipe, bate-papo em grupo ou aplicativo pessoal para um usuário individual. Você pode incluir guias personalizadas com seu aplicativo para incorporar seu próprio conteúdo da Web em Teams ou adicionar funcionalidades específicas de Teams ao seu conteúdo web. Para obter mais informações, consulte [Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client).

Existem dois tipos de guias disponíveis em Teams — canal/grupo e pessoal. As guias de canais/grupos fornecem conteúdo para canais e bate-papos em grupo, e são uma ótima maneira de criar espaços colaborativos em torno de conteúdo dedicado à Web. As guias pessoais, juntamente com bots com escopo pessoal, fazem parte de aplicativos pessoais e são escopo para um único usuário. Eles podem ser fixados na barra de navegação esquerda para fácil acesso.

## <a name="tab-features"></a>Recursos de guia

> [!div class="checklist"]
>
> * Se uma guia for adicionada a um aplicativo que também tenha um bot, o bot também será adicionado à equipe.
> * Conscientização do Azure Active Directory (Azure AD) ID do usuário atual.
> * A conscientização local para que o usuário indique o idioma, ou seja, `en-us` . 
> * Capacidade de digitação única (SSO) se suportada.
> * Capacidade de usar bots ou notificações de aplicativos para vincular profundamente à guia ou a uma sub-entidade dentro do serviço, por exemplo, um item de trabalho individual.
> * A capacidade de abrir um módulo de tarefa a partir de links dentro de uma guia.
> * Reutilização de SharePoint partes da web dentro da guia.

## <a name="tabs-user-scenarios"></a>Tabs cenários de usuário

**Cenário:** Traga um recurso baseado na Web existente dentro de Teams. \
**Exemplo:** Você cria uma guia pessoal em seu aplicativo de Teams que apresenta um site corporativo informativo aos usuários.

**Cenário:** Adicione páginas de suporte a uma extensão de bot ou de mensagens Teams. \
**Exemplo:** Você cria guias pessoais que *fornecem* e *ajudam* o conteúdo da página da Web aos usuários.

**Cenário:** Forneça acesso a itens com os quais seus usuários interagem regularmente para diálogo cooperativo e colaboração. \
**Exemplo:** Você cria uma guia canal/grupo com ligação profunda com itens individuais.

## <a name="understand-how-tabs-work"></a>Entenda como funcionam as guias

Uma guia personalizada é declarada no manifesto do aplicativo do seu pacote de aplicativos. Para cada página da Web que você deseja incluída como uma guia em seu aplicativo, você define uma URL e um escopo. Além disso, você precisa adicionar o [Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client) à sua página e ligar `microsoftTeams.initialize()` após o carregamento da página. Isso dirá ao Teams para exibir sua página, dar-lhe acesso a informações específicas de Teams (por exemplo, se o cliente Teams estiver executando o *tema escuro*), e permitir que você tome medidas com base nos resultados.

Se você optar por expor sua guia dentro do canal/grupo ou escopo pessoal, você precisará apresentar uma página de conteúdo HTML <em \> sua guia. [](~/tabs/how-to/create-tab-pages/content-page.md) Para guias pessoais, a URL de conteúdo é definida diretamente em seu manifesto de aplicativo Teams pela `contentUrl` propriedade no `staticTabs` array. O conteúdo da sua guia será o mesmo para todos os usuários.

Para guias de canal/grupo, você também precisa criar uma página de configuração adicional que permita aos usuários configurar sua URL de página de conteúdo, normalmente usando parâmetros de sequência de perguntas de URL para carregar o conteúdo apropriado para esse contexto. Isso ocorre porque sua guia canal/grupo pode ser adicionada a várias equipes diferentes ou chats em grupo. Em cada instalação subsequente, seus usuários poderão configurar a guia, permitindo que você adapte a experiência conforme necessário. Quando os usuários adicionam ou configuram uma guia, uma URL está sendo associada à guia que é apresentada na interface do Teams UI. Configurar uma guia é simplesmente adicionar parâmetros adicionais a essa URL. Por exemplo, quando você adiciona a guia Azure Boards, a página de configuração permite que você escolha qual placa a guia será carregada. A URL da página de configuração é especificada pela  `configurationUrl` propriedade no array em seu manifesto de `configurableTabs` aplicativo.

Você pode ter vários canais ou guias de grupo, e até dezesseis guias pessoais por aplicativo.

## <a name="mobile-considerations"></a>Considerações móveis

Se você optar por ter seu canal ou aba de grupo aparecendo em Teams clientes móveis, a `setSettings()` configuração deve ter um valor para o `websiteUrl` imóvel. Para garantir a melhor experiência do usuário, você deve seguir as [orientações para guias no celular](~/tabs/design/tabs-mobile.md) ao criar suas guias. Os aplicativos [distribuídos através da loja Teams](~/concepts/deploy-and-publish/appsource/publish.md) têm um processo de aprovação separado para clientes móveis. O comportamento padrão desses aplicativos é o seguinte:

| **Capacidade do aplicativo** | **Comportamento se o aplicativo for aprovado** | **Comportamento se o aplicativo não for aprovado** |
| --- | --- | --- |
| **Guias pessoais** | O aplicativo aparece na barra inferior dos clientes móveis. Estoque e abas Teams cliente. | O aplicativo não aparece na barra inferior dos clientes móveis. |
| **Guias de canais e grupos** | O guia é aberto no Teams cliente usando `contentUrl` . | A aba é aberta em um navegador fora do Teams cliente usando `websiteUrl` . |

> [!NOTE]
>
> O comportamento padrão dos aplicativos só é aplicável se distribuído através da loja Teams. Por padrão, todas as guias se abrem no Teams cliente.
> Para iniciar uma avaliação do seu aplicativo para a simpatia móvel, entre em contato para teamsubm@microsoft.com com os detalhes do seu aplicativo.

## <a name="see-also"></a>Confira também

* [Solicitar permissões do dispositivo](../concepts/device-capabilities/native-device-permissions.md)
* [Integrar recursos de mídia](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integre um QR ou um scanner de código de barras](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrar os recursos de localização](../concepts/device-capabilities/location-capability.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Requisitos de tabulação](~/tabs/how-to/tab-requirements.md)