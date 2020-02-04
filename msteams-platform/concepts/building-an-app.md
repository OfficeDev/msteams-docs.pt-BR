---
title: Criar um aplicativo para o Microsoft Teams
author: clearab
description: Compreenda o processo típico para a criação de um aplicativo para o Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 7c748829c481373dd7dfa011bfba4e7de3aba1bb
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672794"
---
# <a name="building-an-app-for-microsoft-teams"></a>Criar um aplicativo para o Microsoft Teams

Criar e distribuir um aplicativo criado na plataforma do Microsoft Teams envolve decidir o que compilar, criar seus serviços Web, criar um pacote de aplicativos e distribuir esse pacote aos seus usuários finais de destino. Ele será um administrador de uma organização que decidirá quem pode acessar e instalar seu aplicativo, e será até que seus usuários instalem seu aplicativo em qualquer contexto específico.

## <a name="design-a-great-app"></a>Criar um ótimo aplicativo

A etapa mais importante na criação de um aplicativo bem-sucedido para o Microsoft Teams é escolher a combinação certa de pontos de extensibilidade e elementos de interface do usuário para aproveitar. Às vezes, essa é uma decisão bastante fácil, mas para aplicativos mais complexos, você deve gastar bastante tempo entendendo o problema que você está tentando resolver com seu aplicativo e mapeando sua solução entre as várias maneiras pelas quais os usuários podem interagir com seu aplicativo no Microsoft Cliente do teams. Não subestime a importância do contexto e do escopo! Um bot de conversação que funciona muito bem em um chat de um-para-um pode não funcionar como parte de uma conversa de canal ou de chat de grupo.

1. Primeiro, [entenda os pontos de extensibilidade do cliente do Teams e os elementos da interface do usuário](~/concepts/extensibility-points.md) disponíveis para seu aplicativo.

2. Em seguida, certifique-se de que você [entende seus casos de uso](~/concepts/design/understand-use-cases.md).

3. Por fim, [mapeie seus casos de uso para os recursos de plataforma do Microsoft Teams](~/concepts/design/map-use-cases.md).

Depois de decidir quais pontos de extensibilidade e recursos seus aplicativos aproveitarão, você deverá pensar em cada uma dessas interações. Dependendo do design do seu aplicativo, convém examinar:

* [Projetando ótimas guias](~/tabs/design/tabs.md)
* [Projetando bots de conversas úteis](~/bots/design/bots.md)

## <a name="prepare-your-environment"></a>Preparar seu ambiente

Você precisa certificar-se de que tem um ambiente onde pode carregar e testar o aplicativo Teams. Se você ainda não tiver uma assinatura do O365 com o Teams habilitado e a capacidade de carregar aplicativos nele, poderá [se inscrever no programa de desenvolvedor do O365](https://dev.office.com/devprogram) , que fornecerá acesso a uma assinatura gratuita do Office 365 para fins de desenvolvimento.

Consulte [preparar o seu ambiente do O365](~/concepts/build-and-test/prepare-your-o365-tenant.md) para obter mais informações.

## <a name="build-and-test-your-app"></a>Criar e testar seu aplicativo

Criar e testar seu aplicativo para o Microsoft Teams não é muito diferente de criar qualquer outro aplicativo Web. A principal diferença é a necessidade de usar o manifesto do aplicativo em seu pacote de aplicativos para conectar o cliente do teams aos seus serviços Web. Sempre que fizer uma alteração no manifesto do aplicativo, você precisará recarregar seu pacote de aplicativos e atualizar seu aplicativo no Microsoft Teams, reinstalando-o. As alterações no serviço Web no entanto não exigem que você reinstale seu aplicativo no cliente do teams.

Ao criar inicialmente seu aplicativo, você atualizará regularmente os serviços Web e o pacote de aplicativos, geralmente carregando e instalando o aplicativo no cliente do teams várias vezes (particularmente durante a configuração inicial do seu aplicativo). No entanto, conforme o que você está criando estabilizar, a necessidade de alterar o manifesto do aplicativo será reduzida e, principalmente, você fará alterações no serviço Web.

### <a name="build-your-web-services"></a>Criar seus serviços Web

Depois de decidir como os usuários vão interagir com seu aplicativo, seu tempo para criar os serviços Web para poder religá-lo. Dependendo do que você está criando, o Microsoft Teams fornece vários SDKs, modelos, exemplos de código e geradores para ajudá-lo a começar, incluindo:

* SDK da estrutura de bot para [extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) e [bots de conversa](~/bots/what-are-bots.md)
* SDK do cliente JavaScript do teams para [guias](~/tabs/what-are-tabs.md) e outras páginas de conteúdo
* Um [gerador Yeoman](~/tutorials/get-started-yeoman.md) para criar aplicativos no node. js
* **Visualização** Um conjunto de controles de código aberto para suas páginas de conteúdo da Web- [IU fluente](https://microsoft.github.io/fluent-ui-react/)
* [Modelos de aplicativos](~/samples/app-templates.md) prontos para produção
* Várias [amostras](~/samples/code-samples.md) para ajudá-lo a começar

Lembre-se de que você precisará hospedar seus serviços Web de uma maneira que os torne publicamente acessíveis pela Internet (normalmente em um provedor de serviço de nuvem, como o Azure), e sirva o conteúdo via HTTPS.

### <a name="create-your-app-package"></a>Criar seu pacote de aplicativos

Você também precisará criar um pacote de aplicativos que possa ser distribuído e instalado no Microsoft Teams. O pacote de aplicativos contém dois ícones e um arquivo de manifesto JSON que descreve os metadados para seu aplicativo, a extensão aponta que seu aplicativo está usando e aponta para os serviços que ligam esses pontos de extensão.

Ao criar seu pacote de aplicativos, você pode optar por criá-lo manualmente ou usar o app Studio, que é um aplicativo dentro do teams que ajuda você a fazer aplicativos do Teams (sabemos, muito). O app Studio orientará você durante a criação do seu manifesto de aplicativo e poderá ajudá-lo a registrar seu bot com a estrutura de bot. Ele também contém um designer de cartões para ajudá-lo a criar cartões e ações de cartões visualmente e enviar exemplos para si mesmo no Microsoft Teams.

## <a name="distributing-your-app"></a>Distribuindo seu aplicativo

Você tem três opções para [distribuir seu aplicativo do Microsoft Teams](~/concepts/deploy-and-publish/apps-publish.md), dependendo do público-alvo.

* **Compartilhe seu pacote de aplicativos diretamente.** Você pode optar por compartilhar seu pacote de aplicativos diretamente com os usuários. Isso será particularmente útil se o seu aplicativo for direcionado para um público limitado (apenas algumas equipes ou indivíduos) e durante o desenvolvimento e teste do seu aplicativo.
  
* **Publique seu aplicativo em seu catálogo de aplicativos organizacional.** Se seu aplicativo se aplica a uma organização específica (ou se você personalizou seu aplicativo para atender às necessidades específicas de uma organização), um administrador de locatários pode carregar seu aplicativo para o catálogo de aplicativos da organização. Isso disponibiliza o aplicativo para que qualquer pessoa na organização instale (mas não a instale automaticamente).
  
* **Publique seu aplicativo no repositório de aplicativos públicos.** Se o seu aplicativo for destinado a todos os usuários do Microsoft Teams em toda a parte, você poderá enviar seu aplicativo para publicação na loja de aplicativos públicos. Você precisará passar por um processo de revisão rigoroso, portanto, certifique-se de que você está com o seu gosto e cruzou seu t.

Ao distribuir seu aplicativo, você precisa levar em consideração não só o público desejado, mas as políticas de ti em vigor na organização com a qual você deseja compartilhar seu aplicativo. Cada organização tem controle total sobre como determinar quais aplicativos serão carregados no catálogo de aplicativos organizacionais e quais aplicativos estão disponíveis para instalação na loja de aplicativos.

### <a name="the-app-you-create-versus-the-app-your-users-install"></a>O aplicativo que você cria versus o aplicativo que os usuários instalam

Seu aplicativo pode aproveitar os vários pontos de extensibilidade no cliente do Teams e trabalhar em vários escopos. Seu pacote de aplicativos distribuído aos usuários definirá todos eles como uma entidade única. No entanto, como todas as instalações de aplicativos no Microsoft Teams são *específicas de contexto*, a totalidade do seu aplicativo pode nem sempre ser instalada para todos os usuários.

Por exemplo, imagine que seu aplicativo contém um bot de conversa que funciona em conversas pessoais e de equipe, bem como como uma guia pessoal e uma guia canal. Quando seu aplicativo é instalado, ele será instalado em um contexto específico-se um usuário instalar o aplicativo em uma equipe, ele não terá necessariamente instalado a parte pessoal do seu aplicativo. Isso pode ser um pouco confuso em primeiro lugar, apenas lembre-se de nunca esperar que todas as partes do aplicativo sejam instaladas e configuradas em qualquer contexto específico.

## <a name="get-started-quickly"></a>Introdução rápida

Quer começar rapidamente? Confira um dos tutoriais de introdução ou um QuickStart para um recurso de plataforma específica (que pode ser encontrado em cada recurso da documentação).

TUTORIAIS introdutórios:

* [Criar um bot e um aplicativo de guia no C #](~/tutorials/get-started-dotnet-app-studio.md)
* [Criar um bot e um aplicativo de guia em JavaScript/node. js](~/tutorials/get-started-nodejs-app-studio.md)
* [Criar um aplicativo com o gerador Yeoman](~/tutorials/get-started-yeoman.md)
