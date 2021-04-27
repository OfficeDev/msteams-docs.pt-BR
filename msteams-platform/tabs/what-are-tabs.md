---
title: O que são guias personalizadas no Teams?
author: laujan
description: Uma visão geral das guias personalizadas na plataforma teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 4ce17f4d26abfd4fe21b4ac05bb7269fa39a2f7a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020286"
---
# <a name="what-are-microsoft-teams-tabs"></a>O que são guias do Microsoft Teams?

As guias são páginas da Web com conhecimento do Teams inseridas no Microsoft Teams. Eles são marcas html simples <iframe que apontam para domínios declarados no manifesto do aplicativo e podem ser adicionadas como parte de um canal dentro de uma equipe, chat de grupo ou aplicativo pessoal para um usuário \> individual. Você pode incluir guias personalizadas com seu aplicativo para inserir seu próprio conteúdo da Web no Teams ou adicionar funcionalidade específica do Teams ao conteúdo da Web. *Consulte* [SDK do](/javascript/api/overview/msteams-client)cliente JavaScript do Teams.

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão. É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. *Consulte* [o atributo cookie SameSite (atualização 2020)](../resources/samesite-cookie-update.md).

Há dois tipos de guias disponíveis no Teams — canal/grupo e pessoal. As guias canal/grupo oferecem conteúdo para canais e chats de grupo e são uma ótima maneira de criar espaços colaborativos em torno de conteúdo baseado na Web dedicado. Guias pessoais, juntamente com bots de escopo pessoal, fazem parte de aplicativos pessoais e têm escopo para um único usuário. Eles podem ser fixados na barra de navegação esquerda para facilitar o acesso.

## <a name="lesser-known-tab-features"></a>Recursos de tabulação menos conhecidos

> [!div class="checklist"]
>
> * Se uma guia for adicionada a um aplicativo que também tenha um bot, o bot também será adicionado à equipe.
> * Reconhecimento da ID do Azure Active Directory (Azure AD) do usuário atual.
> * Reconhecimento de localidade para que o usuário indique o idioma, ou seja, `en-us` . 
> * Recurso de SSO (SSO) de login único, se for suportado.
> * Capacidade de usar bots ou notificações de aplicativo para vincular profundamente à guia ou a uma sub-entidade dentro do serviço, por exemplo, um item de trabalho individual.
> * A capacidade de abrir um módulo de tarefa a partir de links em uma guia.
> * Reutilização de Web Parts do SharePoint na guia.

## <a name="tabs-user-scenarios"></a>Guias cenários de usuário

**Cenário:** Traga um recurso baseado na Web existente dentro do Teams. \
**Exemplo:** Você cria uma guia pessoal em seu aplicativo do Teams que apresenta um site corporativo informacional aos usuários.

**Cenário:** Adicione páginas de suporte a um bot do Teams ou extensão de mensagens. \
**Exemplo:** Você cria guias pessoais que *fornecem* e ajudam os *usuários* a fornecer conteúdo de página da Web.

**Cenário:** Forneça acesso a itens com os que seus usuários interagem regularmente para diálogo cooperativo e colaboração. \
**Exemplo:** Você cria uma guia canal/grupo com vinculação profunda a itens individuais.

## <a name="how-do-tabs-work"></a>Como funcionam as guias?

Uma guia personalizada é declarada no manifesto do aplicativo do pacote do aplicativo. Para cada página da Web que você deseja incluir como uma guia em seu aplicativo, você define uma URL e um escopo. Além disso, você precisa adicionar o [SDK](/javascript/api/overview/msteams-client) do cliente JavaScript do Teams à sua página e chamar depois que `microsoftTeams.initialize()` a página é carregada. Isso dirá ao Teams para exibir sua página, dar acesso a informações específicas do Teams (por exemplo, se o cliente do Teams estiver executando o tema escuro *)* e permitirá que você tome medidas com base nos resultados.

Se você optar por expor sua guia no escopo de canal/grupo ou pessoal, você precisará apresentar uma página de conteúdo HTML <iframe \> em sua guia. [](~/tabs/how-to/create-tab-pages/content-page.md) Para guias pessoais, a URL de conteúdo é definida diretamente no manifesto do aplicativo do Teams pela `contentUrl` propriedade na `staticTabs` matriz. O conteúdo da guia será o mesmo para todos os usuários.

Para guias de canal/grupo, você também precisa criar uma página de configuração adicional que permita que os usuários configurem a URL da página de conteúdo, normalmente usando parâmetros de cadeia de caracteres de consulta de URL para carregar o conteúdo apropriado para esse contexto. Isso porque sua guia canal/grupo pode ser adicionada a várias equipes ou chats de grupo diferentes. Em cada instalação subsequente, os usuários poderão configurar a guia, permitindo que você adapte a experiência conforme necessário. Quando os usuários adicionam ou configuram uma guia, uma URL está sendo associada à guia apresentada na interface do usuário do Teams. Configurar uma guia é simplesmente adicionar parâmetros adicionais a essa URL. Por exemplo, quando você adiciona a guia Placas do Azure, a página de configuração permite que você escolha qual placa a guia carregará. A URL da página de configuração é especificada pela  `configurationUrl` propriedade na matriz no manifesto do `configurableTabs` aplicativo.

Você pode ter vários canais ou guias de grupo e até dezesseis guias pessoais por aplicativo.

## <a name="mobile-clients"></a>Clientes móveis

Se você optar por que seu canal ou guia de grupo apareça em clientes móveis do Teams, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade. Para garantir a experiência ideal do usuário, você deve seguir as [diretrizes](~/tabs/design/tabs-mobile.md) para guias no celular ao criar suas guias. Os aplicativos [distribuídos por meio do Appsource](~/concepts/deploy-and-publish/appsource/publish.md) têm um processo de aprovação separado para clientes móveis. O comportamento padrão desses aplicativos é o seguinte:

| **Tipo de guia** | **Comportamento do App se ele for otimizado para clientes móveis** | **Comportamento do Aplicativo se ele não for otimizado para clientes móveis** |
|:-----|:-----|:-----|
| **Guias estáticas** ou **guias pessoais**|O aplicativo aparece na barra inferior dos clientes móveis. As guias são abertas em uma webview no aplicativo dentro do cliente do Teams. | O aplicativo não aparece em clientes móveis. |
| **Guias configuráveis** | As guias abrem em um webview no aplicativo dentro do cliente do Teams usando `contentUrl` o . | Selecionar **Guia** abre o conteúdo usando `websiteUrl` o no navegador da Web padrão no dispositivo. |


> [!NOTE]
>
> * [Os aplicativos enviados ao AppSource para publicação no Teams ](../concepts/deploy-and-publish/overview.md#publish-to-appsource) são avaliados automaticamente para a capacidade de resposta móvel. Para qualquer consulta, entre em contato com teamsubm@microsoft.com.
> * Para todos os aplicativos que não são distribuídos por meio do [AppSource](../concepts/deploy-and-publish/overview.md), as guias abrem em uma webview no aplicativo dentro dos clientes do Teams por padrão e não há um processo de aprovação separado necessário.

> [!div class="nextstepaction"]
> [Saiba mais: Solicitar permissões de dispositivo](../concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
> [Saiba mais: Integrar recursos de mídia](../concepts/device-capabilities/mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Saiba mais: Integrar a QR ou o recurso de scanner de código de barras no Teams](../concepts/device-capabilities/qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Saiba mais: Integrar recursos de localização no Teams](../concepts/device-capabilities/location-capability.md)
