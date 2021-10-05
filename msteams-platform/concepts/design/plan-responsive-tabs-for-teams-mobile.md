---
title: Planejar o Teams móvel
author: surbhigupta
description: Guia para planejar a criação de um aplicativo no Teams móvel
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: v-abirade
ms.openlocfilehash: a2c8c601ef2c007c112f1e0e5309f0aa90fce106
ms.sourcegitcommit: 5c0da4f6f24b8ef33da1d235988061546dd324a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/05/2021
ms.locfileid: "60123867"
---
# <a name="plan-responsive-tabs-for-teams-mobile"></a>Planejar guias responsivas para Teams celular

 Teams plataforma oferece a oportunidade de criar aplicativos em dispositivos móveis e desktop. Os usuários do aplicativo podem preferir desktop ou móvel ou ambos. Os usuários podem preparar dados na área de trabalho, mas consumir e compartilhar mais dados usando o celular. A chave para criar qualquer aplicativo é entender e atender às necessidades dos usuários. Há recursos como bots, extensões de mensagens e conectores que funcionam perfeitamente na área de trabalho e em dispositivos móveis. No entanto, a criação de guias e módulos de tarefa exigem planejamento para hospedar sua experiência da Web Teams celular. O documento orienta para planejar suas páginas da Web responsivas Teams celular.

## <a name="identify-apps-scope"></a>Identificar escopo de aplicativos

A lista a seguir fornece as principais informações para planejar a criação de aplicativos para Teams celular:

* Considere a funcionalidade entre dispositivos do Teams app. Por exemplo, se você tiver um aplicativo com bom desempenho na área de trabalho, poderá explorar para criar um aplicativo semelhante em dispositivos móveis. Inicialmente, pode ser difícil mudar toda a experiência da área de trabalho no celular. Você pode começar com cenários básicos, mas comuns. Adicione funcionalidades e recursos depois de coletar mais informações e comentários do usuário.

* Certifique-se de direcionar a persona de usuário apropriada no celular. Por exemplo, se você estiver criando um aplicativo que fornece serviço aos usuários finais e também fornece acesso a dados para desenvolvedores e gerentes sênior, os usuários finais podem usar mais o aplicativo enquanto você começa a criar aplicativos no Teams mobile. Você pode atender a todas as pessoas que você tem em seu aplicativo de área de trabalho, no entanto, é recomendável começar com persona com uma base maior e possíveis adotadores in-loco para uma experiência de tela menor. De acordo com o exemplo, os usuários finais são as personas de usuário apropriadas. Você pode adicionar funcionalidades gradualmente para dar suporte a outras personas de usuário em seu Teams celular. 

## <a name="understand-different-stages-to-build-apps"></a>Compreender diferentes estágios para criar aplicativos

Depois de identificar o escopo do aplicativo, é hora de entender os três estágios a seguir para planejar qualquer aplicativo no Teams móvel e aprimorar a experiência do usuário:

1. **Consumo**

   Exibir aplicativos em dispositivos móveis. Para criar um aplicativo no celular, você pode começar com a experiência de consumo. Como o mundo móvel tornou a rolagem de conteúdo uma prática comum, você pode mostrar informações relevantes. Use mecanismos de envolvimento, como notificações para informar atualizações.

2. **Ações Rápidas**

   Use o aplicativo no celular. Depois que os usuários começarem a consumir o conteúdo em dispositivos móveis, você poderá dimensionar seu aplicativo para o próximo nível migrando algumas ações do aplicativo da área de trabalho. Você pode otimizar e criar novas ações para dispositivos móveis.

3. **Habilitação**

   Forneça experiências completas do aplicativo para se envolver em dispositivos móveis. À medida que os usuários se envolvem com seu aplicativo, forneça uma experiência imersiva completa em dispositivos móveis, em par ou melhor do que a experiência da área de trabalho. Para fornecer uma boa experiência para seus usuários, faça com que todos os casos de uso responsivos no celular.

> [!TIP]
> Para obter informações sobre as diretrizes de design, consulte [processo de design para Teams aplicativos](design-teams-app-process.md).

## <a name="use-cases"></a>Casos de uso

Vamos passar pelos seguintes casos de uso para entender como planejar diferentes tipos de aplicativos para Teams celular:

<br>

<details>

<summary><b>Aplicativos de painel e visualização de dados</b></summary>

Você pode entender como planejar guias responsivas para painéis e aplicativos de visualização de dados Teams plataforma móvel.

**Consumo**

No primeiro estágio, você pode implementar a experiência de consumo mais básica para exibir dados. O objetivo de qualquer aplicativo no domínio é mostrar dados na forma de visualizações. Em seu aplicativo, você pode mostrar visualizações exibidas recentemente na área de trabalho ou lista de todos os gráficos autorizados para os usuários. Depois de criar painéis na área de trabalho, os usuários podem acessar as informações usando o celular. Você pode mostrar uma exibição detalhada de qualquer gráfico selecionado pelo usuário como uma exibição expandida em suas guias ou usando módulos de tarefa.

Você pode mostrar as seguintes informações: 

* Painéis e resumos
* Elementos visuais, mapas e infográficos de dados
* Gráficos, gráficos e tabelas 

![Consumo de aplicativos de painel e visualização de dados](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-consumption.png)

**Ações rápidas**

No segundo estágio, os usuários podem trabalhar nos gráficos e elementos visuais existentes da experiência da área de trabalho. Você pode introduzir as seguintes ações:

* Conteúdo de pesquisa
* Filtrar dados
* Criar indicadores

![Ações rápidas de controle e visualização de dados](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-quick-actions.png)

**Habilitação**

No terceiro estágio, permita que os usuários criem conteúdo como gráficos e gráficos do zero. Certifique-se de apresentar todos os recursos em seu aplicativo para dispositivos móveis. Por exemplo, você pode usar módulos de tarefa para ajudar a acessar itens de dados específicos com exibição detalhada.

Você pode fornecer o seguinte acesso aos usuários:
* Modificar título e descrição
* Inserir itens de dados para criar visualizações
* Compartilhar visualizações em um chat de canal ou grupo

![Habilitação de aplicativos de painel e visualização de dados](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-enablement.png)


<br>

</details>

<br>

<details>

<summary><b>Aplicativos de abordagem de tarefas</b></summary>

Você pode entender como planejar guias responsivas para aplicativos de abordagem de tarefas Teams plataforma móvel.

**Consumo**

No primeiro estágio, seu aplicativo pode mostrar a lista de tarefas para o usuário em uma pilha vertical. Se houver várias categorias de tarefas, como **Proposed**, **Active** e **Closed,** forneça filtros para mostrar tarefas agrupadas ou como headers para ver as tarefas agrupadas.

![Consumo de aplicativos de abordagem de tarefas](../../assets/images/app-fundamentals/taskboarding-apps-consumption.png)

**Ações rápidas**

No segundo estágio, você pode fornecer o seguinte acesso de aplicativo aos usuários:
* Criar tarefas ou itens com os campos obrigatórios para reduzir a carga cognitiva dos usuários
* Alterar o tipo ou o tipo de quadro de exibição
* Revisar tarefas expandindo o exibição
* Usar módulos de tarefa para ver exibição detalhada
* Mover as tarefas para diferentes categorias 
* Compartilhar tarefas relevantes em chats e canais por meio de emails e feed de atividades

![Ações rápidas de aplicativos de abordagem de tarefas](../../assets/images/app-fundamentals/taskboarding-apps-quick-actions.png)

**Habilitação**

No terceiro estágio, você pode habilitar a experiência dos usuários com as seguintes atividades:
* Adicionar novos projetos e placas
* Adicionar e modificar categorias diferentes, como **Proposed**, **Active** e **Closed**
* Configurar as tarefas para comentários, anexos e outros recursos complexos

![Habilitar aplicativos de abordagem de tarefas](../../assets/images/app-fundamentals/taskboarding-apps-enablement.png)
<br>

</details>

<br>

<details>

<summary><b>Coautor e whiteboarding apps</b></summary>

Você pode entender como planejar guias responsivas para aplicativos de coautor e de quadro de trabalho em Teams plataforma móvel.

**Consumo**

No primeiro estágio, você pode considerar a experiência da área de trabalho para mostrar o conteúdo e os ativos em seu aplicativo.  Você pode mostrar as seguintes funções:

* Comentários ou comentários
* Zoom in or out
* Estágio atual ou andamento de um documento pendente

![Consumo de aplicativos de coautor e quadro de trabalho](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-consumption.png)

**Ações Rápidas**

No segundo estágio, você pode introduzir as seguintes ações:

* Criar novo quadro para colaboração ou novos documentos para assinatura
* Compartilhar placas internamente e também com convidados
* Configurar permissões de administrador

> [!TIP]
> Você expõe ações, que podem ser mostradas facilmente nas telas pequenas.

![Ações rápidas de coautor e de whiteboarding apps](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-quick-actions.png)

**Habilitação**

No terceiro estágio, forneça experiência completa aos usuários. Você pode habilitar a experiência dos usuários com as seguintes atividades:

* Adicionando texto, formas e anotações rápidas
* Navegar pelo conteúdo
* Adicionar camadas e filtros
* Excluir, desfazer e refazer operações
* Acesse a câmera e o microfone usando APIs SDK JS. Para obter mais informações sobre os recursos do dispositivo, consulte [Visão geral dos recursos do dispositivo.](../device-capabilities/device-capabilities-overview.md)

![Habilitar aplicativos de coautor e quadro de trabalho](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-enablement.png)

<br>

</details>

## <a name="see-also"></a>Confira também

As seguintes diretrizes de design e validação ajudam dependendo do escopo do seu aplicativo:

* [Projetando sua guia](../../tabs/design/tabs.md)
* [Projetando um bot](../../bots/design/bots.md)
* [Criar módulos de tarefa](../..//task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [Validando diretrizes](../deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)
