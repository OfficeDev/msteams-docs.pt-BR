---
title: Planejar o Teams para dispositivos móveis
author: surbhigupta
description: Com este módulo de aprendizado, você aprenderá a planejar a criação de um aplicativo no Teams móvel e a entender diferentes estágios para criar o aplicativo.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: v-abirade
ms.openlocfilehash: 22b3abc44b2996547bc05e8cd11458b00eed1436
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143183"
---
# <a name="plan-responsive-tabs-for-teams-mobile"></a>Planejar guias responsivas para o aplicativo móvel do Teams

 A plataforma Teams oferece a oportunidade de criar aplicativos em dispositivos móveis e desktop. Os usuários do aplicativo podem preferir a área de trabalho ou móvel ou ambos. Os usuários podem preparar dados na área de trabalho, mas consumir e compartilhar mais dados usando dispositivos móveis. A chave para criar qualquer aplicativo é entender e atender às necessidades dos usuários. Há recursos como bots, extensões de mensagem e conectores que funcionam perfeitamente na área de trabalho e em dispositivos móveis. No entanto, a criação de guias e módulos de tarefas exige o planejamento para hospedar sua experiência na Web no Teams Mobile. O artigo orienta para planejar suas páginas da Web responsivas no Teams Mobile.

## <a name="identify-apps-scope"></a>Identificar escopo de aplicativos

A lista a seguir fornece as principais informações para planejar a criação de aplicativos para o Teams Mobile:

* Considere a funcionalidade entre dispositivos do aplicativo Teams. Por exemplo, se você tiver um aplicativo de bom desempenho na área de trabalho, poderá explorar para criar um aplicativo semelhante em dispositivos móveis. Inicialmente, pode ser difícil mudar toda a experiência da área de trabalho em dispositivos móveis. Você pode começar com cenários básicos, mas comuns. Adicione funcionalidades e funcionalidades depois de coletar mais insights e comentários do usuário.

* Certifique-se de direcionar a persona de usuário apropriada no celular. Por exemplo, se você estiver criando um aplicativo que fornece serviço aos usuários finais e também fornece acesso a dados para desenvolvedores e gerentes sêniores, os usuários finais poderão usar mais o aplicativo enquanto você começa a criar aplicativos no Teams Mobile. Você pode atender a todas as personas que você tem em seu aplicativo da área de trabalho, no entanto, é recomendável começar com persona com uma base maior e possíveis usuários pioneiros para uma experiência de tela menor. De acordo com o exemplo, os usuários finais são as personas de usuário apropriadas. Você pode adicionar funcionalidades gradualmente para dar suporte a outras personas de usuário em seu dispositivo móvel do Teams.

## <a name="understand-different-stages-to-build-apps"></a>Entender os diferentes estágios para criar aplicativos

Depois de identificar o escopo do aplicativo, é hora de entender os três estágios a seguir para planejar qualquer aplicativo no Teams Mobile e aprimorar a experiência do usuário:

1. **Consumo**

   Exibir aplicativos em dispositivos móveis. Para criar um aplicativo em dispositivos móveis, você pode começar com a experiência de consumo. Como o mundo móvel tornou a rolagem de conteúdo uma prática comum, você pode mostrar informações relevantes. Use mecanismos de envolvimento, como notificações para informar as atualizações.

2. **Ações Rápidas**

   Use o aplicativo no celular. Depois que os usuários começarem a consumir o conteúdo em dispositivos móveis, você poderá dimensionar seu aplicativo para o próximo nível migrando algumas ações do aplicativo da área de trabalho. Você pode otimizar e criar novas ações para dispositivos móveis.

3. **Habilitação**

   Forneça experiências completas de aplicativo para se envolver em dispositivos móveis. À medida que os usuários se envolvem com seu aplicativo, forneça uma experiência imersiva completa em dispositivos móveis, seja em par ou melhor do que a experiência desktop. Para fornecer uma boa experiência para seus usuários, torne todos os casos de uso responsivos em dispositivos móveis.

> [!TIP]
> Para obter informações sobre as diretrizes de design, consulte [processo de design para aplicativos do Teams](design-teams-app-process.md).

## <a name="use-cases"></a>Casos de uso

Vamos examinar os seguintes casos de uso para entender como planejar diferentes tipos de aplicativos para o Teams Mobile:

<br>

<details>

<summary><b>Aplicativos de visualização de dados e criação de painéis</b></summary>

Você pode entender como planejar guias responsivas para aplicativos de visualização de dados e criação de painéis na plataforma móvel do Teams.

Consumo:

No primeiro estágio, você pode implementar a experiência de consumo mais básica para exibir dados. A finalidade de qualquer aplicativo no domínio é mostrar dados na forma de visualizações. Em seu aplicativo, você pode mostrar visualizações exibidas recentemente na área de trabalho ou lista de todos os gráficos autorizados para os usuários. Depois de criar painéis na área de trabalho, os usuários podem acessar as informações usando dispositivos móveis. Você pode mostrar uma exibição detalhada de qualquer gráfico selecionado pelo usuário como uma exibição expandida em suas guias ou usando módulos de tarefa.

Você pode mostrar as seguintes informações:

* Dashboards e resumos.
* Visuais de dados, mapas e infográficos.
* Gráficos, gráficos e tabelas.

![Consumo de aplicativos de visualização de dados e criação de painéis](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-consumption.png)

Ações rápidas:

No segundo estágio, os usuários podem trabalhar nos gráficos e visuais existentes da experiência desktop. Você pode introduzir as seguintes ações:

* Pesquisar conteúdo.
* Filtrar dados.
* Criar indicadores.

![Ações rápidas de aplicativos de visualização de dados e criação de painéis](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-quick-actions.png)

Capacitação:

No terceiro estágio, permita que os usuários criem conteúdo como gráficos e gráficos do zero. Certifique-se de introduzir todos os recursos em seu aplicativo para dispositivos móveis. Por exemplo, você pode usar módulos de tarefa para ajudar a acessar itens de dados específicos com exibição detalhada.

Você pode fornecer o seguinte acesso aos usuários:

* Modifique o título e a descrição.
* Inserir itens de dados para criar visualizações.
* Compartilhe visualizações em um canal ou chat em grupo.

![Habilitação de aplicativos de visualização de dados e criação de painéis](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-enablement.png)

<br>

</details>

<br>

<details>

<summary><b>Aplicativos de integração de tarefas</b></summary>

Você pode entender como planejar guias responsivas para aplicativos de integração de tarefas na plataforma móvel do Teams.

Consumo:

No primeiro estágio, seu aplicativo pode mostrar a lista de tarefas para o usuário em uma pilha vertical. Se houver várias categorias de tarefas, como **Proposta**, **Ativa** e **Fechada**, forneça filtros para mostrar tarefas agrupadas ou como cabeçalhos para ver as tarefas agrupadas.

![Consumo de aplicativos de integração de tarefas](../../assets/images/app-fundamentals/taskboarding-apps-consumption.png)

Ações rápidas:

No segundo estágio, você pode fornecer o seguinte acesso de aplicativo aos usuários:

* Crie tarefas ou itens com os campos obrigatórios para reduzir a carga cognitiva dos usuários.
* Altere o tipo de quadro ou o modo de exibição.
* Examine as tarefas expandindo a exibição.
* Use módulos de tarefa para ver a exibição detalhada.
* Mova as tarefas para categorias diferentes.
* Compartilhe tarefas relevantes em chats e canais por meio de emails e feed de atividades.

![Ações rápidas de aplicativos de integração de tarefas](../../assets/images/app-fundamentals/taskboarding-apps-quick-actions.png)

Capacitação:

No terceiro estágio, você pode habilitar a experiência dos usuários com as seguintes atividades:

* Adicione novos projetos e quadros.
* Adicione e modifique categorias diferentes, como **Proposta**, **Ativa** e **Fechada**.
* Configure as tarefas para comentários, anexos e outros recursos complexos.

![Habilitação de aplicativos de integração de tarefas](../../assets/images/app-fundamentals/taskboarding-apps-enablement.png)
<br>

</details>

<br>

<details>

<summary><b>Aplicativos de coautoria e quadro de comunicações</b></summary>

Você pode entender como planejar guias responsivas para coautoria e aplicativos de quadro de comunicações na plataforma móvel do Teams.

Consumo:

No primeiro estágio, você pode considerar a experiência desktop para mostrar o conteúdo e os ativos em seu aplicativo.  Você pode mostrar as seguintes funções:

* Comentários ou comentários.
* Ampliar ou reduzir.
* Estágio atual ou progresso de um documento pendente.

![Consumo de aplicativos de coautoria e quadro de comunicações](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-consumption.png)

Ações Rápidas:

No segundo estágio, você pode introduzir as seguintes ações:

* Crie um novo quadro para colaboração ou novos documentos para assinatura.
* Compartilhe quadros internamente e também com convidados.
* Configurar permissões de administrador.

> [!TIP]
> Você expõe ações, que podem ser mostradas facilmente nas telas pequenas.

![Ações rápidas de coautoria e de aplicativos de quadro de comunicações](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-quick-actions.png)

Capacitação:

No terceiro estágio, forneça experiência completa aos usuários. Você pode habilitar a experiência dos usuários com as seguintes atividades:

* Adicionando texto, formas e anotações rápidas.
* Navegue pelo conteúdo.
* Adicionar camadas e filtros.
* Excluir, desfazer e refazer operações.
* Acesse a câmera e o microfone usando APIs do SDK do JS. Para obter mais informações sobre os recursos do dispositivo, consulte [visão geral dos recursos de dispositivo](../device-capabilities/device-capabilities-overview.md).

![Habilitação de aplicativos de coautoria e quadro de comunicações](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-enablement.png)

<br>

</details>

## <a name="see-also"></a>Confira também

As seguintes diretrizes de design e validação ajudam dependendo do escopo do seu aplicativo:

* [Criar sua guia](../../tabs/design/tabs.md)
* [Criar um bot](../../bots/design/bots.md)
* [Criar módulos de tarefa](../..//task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [Diretrizes de validação da loja](../deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)
