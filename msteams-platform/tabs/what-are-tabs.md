---
title: Guias do Microsoft Teams
author: surbhigupta
description: Aprenda a criar guias, páginas da Web inseridas no Microsoft Teams. Crie uma página de conteúdo como parte da guia pessoal, canal ou grupo. Além disso, aprenda a criar guias com Cartões Adaptáveis.
ms.localizationpriority: high
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: cd8e57a0773a5c1b8cd145176de703018c4e45e7
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68819986"
---
# <a name="build-tabs-for-teams"></a>Compilar guias para o Teams

As guias são páginas da Web compatíveis com o Microsoft Teams incorporadas ao Microsoft Teams. Elas são marcas de `<iframe\>` HTML simples que apontam para domínios declarados no manifesto do aplicativo e podem ser adicionadas como parte de um canal dentro de uma equipe, chat em grupo ou aplicativo pessoal para um usuário individual. Você pode incluir guias personalizadas com seu aplicativo para inserir seu próprio conteúdo da Web no Teams ou adicionar funcionalidades específicas do Teams ao conteúdo da Web. Para mais informações, veja o [Cliente SDK JavaScript do Teams](/javascript/api/overview/msteams-client).

> [!IMPORTANT]
> Atualmente, as guias personalizadas estão disponíveis Nuvem da Comunidade Governamental (GCC), GCC-High e DoD (Departamento de Defesa).

A imagem a seguir mostra guias pessoais:

:::image type="content" source="../assets/images/tabs/personaltab.png" alt-text="A captura de tela mostra um exemplo de uma guia pessoal no cliente da área de trabalho do Teams.":::

A imagem a seguir mostra as guias do canal Contoso:

:::image type="content" source="../assets/images/tabs/tabs.png" alt-text="Guias de canal ou grupo" lightbox="../assets/images/tabs/tabs.png":::

Há alguns pré-requisitos pelos quais você deve passar antes de trabalhar nas guias.

Há dois tipos de guias disponíveis no Teams, pessoal e canal ou grupo. [Guias pessoais](~/tabs/how-to/create-personal-tab.md), junto com bots de conversação direta, fazem parte de aplicativos pessoais e têm como escopo um único usuário. Eles podem ser fixados na barra de navegação à esquerda para facilitar o acesso. [Canal ou guias de grupo](~/tabs/how-to/create-channel-group-tab.md) forneça conteúdo para canais e chats em grupo e é uma ótima maneira de criar espaços colaborativos em torno de conteúdo dedicado baseado na web.

Você pode [criar uma página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) como parte de uma guia pessoal, canal ou guia de grupo ou módulo de tarefa. Você pode [criar uma página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md) que permite aos usuários configurar o aplicativo Microsoft Teams e usá-lo para configurar uma guia de chat de canal ou grupo, uma extensão de mensagens ou um Conector do Office 365. Você pode permitir que os usuários reconfigurem sua guia após a instalação e [criar uma página de remoção de guia](~/tabs/how-to/create-tab-pages/removal-page.md) para seu aplicativo. Ao criar um aplicativo do Teams que inclui uma guia, você deve testar como seu [guia nos clientes do Teams para Android e iOS](~/tabs/design/tabs-mobile.md). Sua guia deve [ter contexto](~/tabs/how-to/access-teams-context.md) por meio de informações básicas, informações de localidade e tema e `entityId` ou `subEntityId` que identifica o que está na guia.

Você pode criar guias com Cartões Adaptáveis centralizar todos os recursos de aplicativo do Teams eliminando a necessidade de um back-end diferente para seus bots e guias. O [Modo de exibição de Estágio](~/tabs/tabs-link-unfurling.md) é um novo componente de Interface do Usuário que permite renderizar o conteúdo aberto em tela inteira no Teams e fixado como uma guia. O serviço [desenrolamento de link](~/tabs/tabs-link-unfurling.md) existente é atualizado, para que ele seja usado para transformar URLs em uma guia usando um Cartão Adaptável e Serviços de Chat. Você pode [criar guias de conversação](~/tabs/how-to/conversational-tabs.md) usando subentidades de conversa que permitem que os usuários tenham conversas sobre subentidades em sua guia, como tarefa específica, paciente e oportunidade de vendas, em vez de discutir a guia inteira. Você pode fazer alterações na [margens da guia](~/resources/removing-tab-margins.md) para aprimorar a experiência do desenvolvedor ao criar aplicativos. Você pode arrastar a guia e colocá-la na posição desejada para alternar as posições da guia em seus aplicativos pessoais e chats de canal ou grupo.

> [!NOTE]
> **Postagens** e **Arquivos** que não podem ser movidos de suas posições.

## <a name="tab-features"></a>Recursos da guia

Os recursos da guia são os seguintes:

* Se uma guia for adicionada a um aplicativo que também tem um bot, o bot também será adicionado à equipe.
* Reconhecimento da ID do Microsoft Azure Active Directory (Azure AD) do usuário atual.
* Reconhecimento de localidade para o usuário indicar o idioma `en-us`.
* Funcionalidade de SSO (logon único), se houver suporte.
* Capacidade de usar bots ou notificações de aplicativo para vincular profundamente à guia ou a uma sub-entidade dentro do serviço, por exemplo, um item de trabalho individual.
* A capacidade de abrir um módulo de tarefa de links em uma guia.
* Reutilização de Web Parts do SharePoint na guia.

## <a name="tabs-user-scenarios"></a>Guias de cenários de usuário

**Cenário:** Traga um recurso web existente para o Teams. \
**Exemplo:** Você cria uma guia pessoa no seu app Teams que apresenta um website informacional aos usuários.

**Cenário:** Adicione páginas de suporte a um bot ou extensão de mensagens do Teams. \
**Exemplo:** Você cria guias pessoais que fornecem **sobre** e **ajuda** conteúdo da página da web aos usuários.

**Cenário:** Forneça acesso aos itens com os quais os usuários interagem regularmente para diálogo cooperativo e colaboração. \
**Exemplo:** Você cria uma guia de canal ou grupo com vinculação profunda a itens individuais.

## <a name="understand-how-tabs-work"></a>Entender como as guias funcionam

Você pode usar um dos seguintes métodos para criar guias:

* [Declarar guias personalizadas no manifesto do aplicativo](#declare-custom-tab-in-app-manifest)
* [Use o Cartão Adaptativo para construir guias](~/tabs/how-to/build-adaptive-card-tabs.md)

### <a name="declare-custom-tab-in-app-manifest"></a>Declarar guia personalizada no manifesto do aplicativo

Uma guia personalizada é declarada no manifesto do aplicativo do pacote do aplicativo. Para cada página da web que você deseja incluir como uma guia em seu aplicativo, defina uma URL e um escopo. Além disso, você pode adicionar o [SDK cliente JavaScript do Teams](/javascript/api/overview/msteams-client) à sua página, e ligar `microsoftTeams.initialize()` após o carregamento de sua página. O Teams exibe sua página e fornece acesso a informações específicas do Teams, por exemplo, o cliente do Teams está executando o tema escuro.

Whether you choose to expose your tab within the channel or group, or personal scope, you must present an <iframe\> HTML [content page](~/tabs/how-to/create-tab-pages/content-page.md) in your tab. For personal tabs, the content URL is set directly in your Teams app manifest by the `contentUrl` property in the `staticTabs` array. Your tab's content is the same for all users.

Para guias de canal ou grupo, você também pode criar uma página de configuração extra. Esta página permite configurar a URL da página de conteúdo, normalmente usando parâmetros de cadeia de caracteres de consulta de URL para carregar o conteúdo apropriado para esse contexto. Isso ocorre porque seu canal ou guia de grupo pode ser adicionado a várias equipes ou chats em grupo. Em cada instalação subsequente, os usuários podem configurar a guia, permitindo que você personalize a experiência conforme necessário. Quando os usuários adicionam ou configuram uma guia, uma URL é associada à guia apresentada na interface do usuário do Teams. A configuração de uma guia simplesmente adiciona mais parâmetros a essa URL. Por exemplo, quando você adiciona a guia Azure Boards, a página de configuração permite que você escolha qual placa a guia carrega. A URL da página de configuração é especificada pela `configurationUrl` propriedade na `configurableTabs` matriz em seu manifesto de aplicação.

Você pode ter vários canais ou guias de grupo e até 16 guias pessoais por aplicativo.

### <a name="tools-to-build-tabs"></a>Ferramentas para criar guias

* [Kit de ferramentas do Teams para Visual Studio Code](../toolkit/teams-toolkit-fundamentals.md)
* [Kit de ferramentas do Teams para Visual Studio](../toolkit/visual-studio-overview.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Pré-requisitos](~/tabs/how-to/tab-requirements.md)

## <a name="see-also"></a>Confira também

* [Projete sua guia para o Microsoft Teams](design/tabs.md)
* [Funcionalidades de dispositivo](../concepts/device-capabilities/device-capabilities-overview.md)
* [Guias em dispositivos móveis](design/tabs-mobile.md#tabs-on-mobile)
* [Funcionalidades do aplicativo mapeados para recursos](../concepts/design/map-use-cases.md#app-capabilities-mapped-to-features)
