---
title: O que são guias personalizadas no Teams?
author: laujan
description: Uma visão geral das guias personalizadas na plataforma do Teams
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 64c6e44177f1fb598895f748dbd0ec1c0b1e3aa1
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797887"
---
# <a name="what-are-microsoft-teams-tabs"></a>O que são guias do Microsoft Teams?

As guias são páginas da Web com suporte para o Teams inseridas no Microsoft Teams. Eles são marcas html <iframe simples que apontam para domínios declarados no manifesto do aplicativo e podem ser adicionadas como parte de um canal dentro de uma equipe, chat em grupo ou aplicativo pessoal para um \> usuário individual. Você pode incluir guias personalizadas com seu aplicativo para inserir seu próprio conteúdo da Web no Teams ou adicionar funcionalidades específicas do Teams ao conteúdo da Web. *Confira* [o SDK do cliente JavaScript do Teams.](/javascript/api/overview/msteams-client)

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, apresenta novos valores de cookie e impõe políticas de cookie por padrão. É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. *Veja* [o atributo de cookie SameSite (atualização de 2020).](../resources/samesite-cookie-update.md)

Há dois tipos de guias disponíveis no Teams: canal/grupo e pessoal. As guias canal/grupo oferecem conteúdo para canais e chats em grupo e são uma ótima maneira de criar espaços colaborativos em torno de conteúdo dedicado baseado na Web. Guias pessoais, juntamente com bots com escopo pessoal, fazem parte de aplicativos pessoais e têm como escopo um único usuário. Eles podem ser fixados na barra de navegação esquerda para facilitar o acesso.

## <a name="lesser-known-tab-features"></a>Recursos de guia menos conhecidos

> [!div class="checklist"]
>
> * Se uma guia for adicionada a um aplicativo que também tenha um bot, o bot também será adicionado à equipe.
> * Reconhecimento da ID do usuário atual do Azure Active Directory (Azure AD).
> * Reconhecimento de localidade para o usuário indicar o idioma, ou seja, `en-us` . 
> * Funcionalidade de SSO (single sign-on), se tiver suporte.
> * Capacidade de usar bots ou notificações de aplicativo para vincular profundamente à guia ou a uma sub-entidade dentro do serviço, por exemplo, um item de trabalho individual.
> * A capacidade de abrir um módulo de tarefa a partir de links em uma guia.
> * Reutilização de Web Parts do SharePoint na guia.

## <a name="tabs-user-scenarios"></a>Cenários de usuário de guias

**Cenário:** Traga um recurso existente baseado na Web para o Teams. \
**Exemplo:** Você cria uma guia pessoal em seu aplicativo do Teams que apresenta um site corporativo informacional aos usuários.

**Cenário:** Adicione páginas de suporte a um bot do Teams ou extensão de mensagens. \
**Exemplo:** Você cria guias pessoais que fornecem sobre *e* *ajudam o* conteúdo da página da Web aos usuários.

**Cenário:** Forneça acesso a itens com os que seus usuários interagem regularmente para diálogo cooperativo e colaboração. \
**Exemplo:** Você cria uma guia de canal/grupo com vinculação profunda a itens individuais.

## <a name="how-do-tabs-work"></a>Como funcionam as guias?

Uma guia personalizada é declarada no manifesto do aplicativo do pacote do aplicativo. Para cada página da Web que você deseja incluir como uma guia em seu aplicativo, defina uma URL e um escopo. Além disso, você precisa adicionar o [SDK](/javascript/api/overview/msteams-client) do cliente JavaScript do Teams à sua página e chamar depois que `microsoftTeams.initialize()` a página é carregada. Fazer isso dirá ao Teams para exibir sua página, lhe dará acesso a informações específicas do Teams (por exemplo, se o cliente do Teams estiver executando o tema *escuro)* e permitirá que você tome uma ação com base nos resultados.

Se você optar por expor sua guia dentro do canal/grupo ou escopo pessoal, precisará apresentar uma página de conteúdo HTML <iframe \> em sua guia. [](~/tabs/how-to/create-tab-pages/content-page.md) Para guias pessoais, a URL de conteúdo é definida diretamente no manifesto do aplicativo Teams `contentUrl` pela propriedade na `staticTabs` matriz. O conteúdo da guia será o mesmo para todos os usuários.

Para guias de canal/grupo, você também precisa criar uma página de configuração adicional que permita que os usuários configurem a URL da página de conteúdo, normalmente usando parâmetros de cadeia de caracteres de consulta url para carregar o conteúdo apropriado para esse contexto. Isso porque a guia canal/grupo pode ser adicionada a várias equipes ou chats em grupo diferentes. Em cada instalação subsequente, os usuários poderão configurar a guia, permitindo que você adapte a experiência conforme necessário. Quando os usuários adicionam ou configuram uma guia, uma URL está sendo associada à guia apresentada na interface do usuário do Teams. Configurar uma guia é simplesmente adicionar parâmetros adicionais a essa URL. Por exemplo, quando você adiciona a guia Painéis do Azure, a página de configuração permite escolher qual quadro a guia será carregada. A URL da página de configuração é especificada  `configurationUrl` pela propriedade na matriz no manifesto do `configurableTabs` aplicativo.

Você pode ter no máximo uma (1) guia canal/grupo e até dezesseis (16) guias pessoais por aplicativo.

## <a name="mobile-clients"></a>Clientes móveis

Se você optar por que seu canal ou guia de grupo apareça em clientes móveis do Teams, a configuração deverá `setSettings()` ter um valor para a `websiteUrl` propriedade. Para garantir a experiência ideal do usuário, você deve seguir as orientações para guias em [dispositivos](~/tabs/design/tabs-mobile.md) móveis ao criar suas guias. Os aplicativos [distribuídos por meio do Appsource](~/concepts/deploy-and-publish/appsource/publish.md) têm um processo de aprovação separado para clientes móveis. O comportamento padrão desses aplicativos é o seguinte:

| **Funcionalidade do aplicativo** | **Comportamento se o aplicativo for aprovado** | **Comportamento se o aplicativo não for aprovado** |
| --- | --- | --- |
| **Guias estáticas** | O aplicativo aparece na barra inferior dos clientes móveis. As guias são abertas no cliente do Teams. | O aplicativo não aparece na barra inferior dos clientes móveis. |
| **Guias configuráveis** | A guia é aberta no cliente do Teams `contentUrl` usando. | A guia é aberta em um navegador fora do cliente do Teams `websiteUrl` usando. |


>[!NOTE]
>
>- O comportamento padrão dos aplicativos só será aplicável se eles são distribuídos por meio do AppSource. Não há processo de aprovação para aplicativos distribuídos por meio de outros [métodos de distribuição.](~/concepts/deploy-and-publish/overview.md) Por padrão, todas as guias são abertas no cliente do Teams.
>- Para iniciar uma avaliação do seu aplicativo para dispositivos móveis, entre em contato teamsubm@microsoft.com os detalhes do aplicativo.


> [!div class="nextstepaction"]
> [Saiba mais: Solicitar permissões de dispositivo](/concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
>[Saiba mais: Permissões de câmera e galeria de imagens](/concepts/device-capabilities/mobile-camera-image-permissions.md)
