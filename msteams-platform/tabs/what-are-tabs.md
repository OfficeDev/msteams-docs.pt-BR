---
title: O que são guias personalizadas Teams?
author: laujan
description: Uma visão geral das guias personalizadas na Teams plataforma
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 21499a4e18acee369b4b1bda6184e4b14b6262ec
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52629967"
---
# <a name="microsoft-teams-tabs"></a>Guias do Microsoft Teams

As guias são Teams web com conhecimento de Microsoft Teams. Eles são marcas html simples <iframe que apontam para domínios declarados no manifesto do aplicativo e podem ser adicionadas como parte de um canal dentro de uma equipe, chat de grupo ou aplicativo pessoal para um usuário \> individual. Você pode incluir guias personalizadas com seu aplicativo para inserir seu próprio conteúdo da Web Teams ou adicionar uma funcionalidade específica Teams ao conteúdo da Web. Para obter mais informações, [consulte Teams SDK do cliente JavaScript.](/javascript/api/overview/msteams-client)

Há dois tipos de guias disponíveis no Teams — canal/grupo e pessoal. As guias canal/grupo oferecem conteúdo para canais e chats de grupo e são uma ótima maneira de criar espaços colaborativos em torno de conteúdo baseado na Web dedicado. Guias pessoais, juntamente com bots de escopo pessoal, fazem parte de aplicativos pessoais e têm escopo para um único usuário. Eles podem ser fixados na barra de navegação esquerda para facilitar o acesso.

## <a name="tab-features"></a>Recursos de tabulação

> [!div class="checklist"]
>
> * Se uma guia for adicionada a um aplicativo que também tenha um bot, o bot também será adicionado à equipe.
> * Reconhecimento da Azure Active Directory (Azure AD) ID do usuário atual.
> * Reconhecimento de localidade para que o usuário indique o idioma, ou seja, `en-us` . 
> * Recurso de SSO (SSO) de login único, se for suportado.
> * Capacidade de usar bots ou notificações de aplicativo para vincular profundamente à guia ou a uma sub-entidade dentro do serviço, por exemplo, um item de trabalho individual.
> * A capacidade de abrir um módulo de tarefa a partir de links em uma guia.
> * Reutilização de SharePoint web parts na guia.

## <a name="tabs-user-scenarios"></a>Guias cenários de usuário

**Cenário:** Traga um recurso baseado na Web existente para dentro Teams. \
**Exemplo:** Você cria uma guia pessoal em seu aplicativo Teams que apresenta um site corporativo informacional aos usuários.

**Cenário:** Adicione páginas de suporte a um bot Teams ou extensão de mensagens. \
**Exemplo:** Você cria guias pessoais que *fornecem* e ajudam os *usuários* a fornecer conteúdo de página da Web.

**Cenário:** Forneça acesso a itens com os que seus usuários interagem regularmente para diálogo cooperativo e colaboração. \
**Exemplo:** Você cria uma guia canal/grupo com vinculação profunda a itens individuais.

## <a name="understand-how-tabs-work"></a>Entender como as guias funcionam

Uma guia personalizada é declarada no manifesto do aplicativo do pacote do aplicativo. Para cada página da Web que você deseja incluir como uma guia em seu aplicativo, você define uma URL e um escopo. Além disso, você precisa adicionar o [Teams SDK](/javascript/api/overview/msteams-client) do cliente JavaScript à sua página e chamar depois que `microsoftTeams.initialize()` a página é carregada. Fazer isso dirá Teams exibir sua página, lhe dará acesso Teams informações específicas (por exemplo, se o cliente Teams estiver executando o tema escuro *)* e permitirá que você tome medidas com base nos resultados.

Se você optar por expor sua guia no escopo de canal/grupo ou pessoal, você precisará apresentar uma página de conteúdo HTML <iframe \> em sua guia. [](~/tabs/how-to/create-tab-pages/content-page.md) Para guias pessoais, a URL de conteúdo é definida diretamente no manifesto do aplicativo Teams pela `contentUrl` propriedade na `staticTabs` matriz. O conteúdo da guia será o mesmo para todos os usuários.

Para guias de canal/grupo, você também precisa criar uma página de configuração adicional que permita que os usuários configurem a URL da página de conteúdo, normalmente usando parâmetros de cadeia de caracteres de consulta de URL para carregar o conteúdo apropriado para esse contexto. Isso porque sua guia canal/grupo pode ser adicionada a várias equipes ou chats de grupo diferentes. Em cada instalação subsequente, os usuários poderão configurar a guia, permitindo que você adapte a experiência conforme necessário. Quando os usuários adicionam ou configuram uma guia, uma URL está sendo associada à guia apresentada na interface do usuário Teams usuário. Configurar uma guia é simplesmente adicionar parâmetros adicionais a essa URL. Por exemplo, quando você adiciona a guia Azure Boards, a página de configuração permite escolher qual placa a guia carregará. A URL da página de configuração é especificada pela  `configurationUrl` propriedade na matriz no manifesto do `configurableTabs` aplicativo.

Você pode ter vários canais ou guias de grupo e até dezesseis guias pessoais por aplicativo.

## <a name="mobile-considerations"></a>Considerações sobre dispositivos móveis

Se você optar por fazer com que seu canal ou guia de grupo apareça Teams clientes móveis, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade. Para garantir a experiência ideal do usuário, você deve seguir as [diretrizes](~/tabs/design/tabs-mobile.md) para guias no celular ao criar suas guias. Os [aplicativos distribuídos pelo Teams têm](~/concepts/deploy-and-publish/appsource/publish.md) um processo de aprovação separado para clientes móveis. O comportamento padrão desses aplicativos é o seguinte:

| **Funcionalidade do aplicativo** | **Comportamento se o aplicativo for aprovado** | **Comportamento se o aplicativo não for aprovado** |
| --- | --- | --- |
| **Guias pessoais** | O aplicativo aparece na barra inferior dos clientes móveis. Guias abertas no cliente Teams cliente. | O aplicativo não aparece na barra inferior dos clientes móveis. |
| **Guias de canal e grupo** | A guia é aberta no cliente Teams usando `contentUrl` . | A guia é aberta em um navegador fora do Teams cliente usando `websiteUrl` . |

> [!NOTE]
>
> O comportamento padrão dos aplicativos só será aplicável se for distribuído por meio do Teams store. Por padrão, todas as guias são abertas no Teams cliente.
> Para iniciar uma avaliação do seu aplicativo para dispositivos móveis, entre em contato com teamsubm@microsoft.com com os detalhes do aplicativo.

## <a name="see-also"></a>Confira também

* [Solicitar permissões do dispositivo](../concepts/device-capabilities/native-device-permissions.md)
* [Integrar recursos de mídia](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrar uma QR ou um scanner de código de barras](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrar os recursos de localização](../concepts/device-capabilities/location-capability.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Requisitos de tabulação](~/tabs/how-to/tab-requirements.md)
