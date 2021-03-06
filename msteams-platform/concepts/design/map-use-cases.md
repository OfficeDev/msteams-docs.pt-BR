---
title: Mapear seus casos de uso para Teams de aplicativos
author: surbhigupta
description: Identifique como os casos de uso do seu aplicativo podem funcionar dentro da experiência Teams experiência.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: b374f0ca81402effb548c1cfcb90ed3d316360f1
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068557"
---
# <a name="map-your-use-cases-to-teams-app-capabilities"></a>Mapear seus casos de uso para Teams de aplicativos

Depois de identificar *quem* é o usuário e *qual* problema você resolverá, é hora de decidir *como* resolver o problema. Quem , *o que* e *como* conclui o processo de compreensão e mapeamento de seus casos de uso para Teams aplicativos. Você precisa definir o escopo do aplicativo com base nas respostas recebidas do usuário para suas consultas e, em seguida, decidir qual recurso é mais adequado para criar seu aplicativo.

> [!NOTE]
> Você deve ter uma boa compreensão dos pontos de entrada e dos elementos [de interface](../../concepts/extensibility-points.md) do usuário disponíveis para seu aplicativo. Você também deve se certificar de considerar [cuidadosamente seus casos de](../../concepts/design/understand-use-cases.md) uso.

## <a name="choose-the-correct-scope-for-your-app"></a>Escolha o escopo correto para seu aplicativo

Ao escolher o escopo do aplicativo, considere o seguinte:

* Um aplicativo pode existir entre escopos.
* Os recursos do aplicativo, como extensões de mensagens, seguem os usuários em todos os escopos.
* Os usuários geralmente não podem adicionar aplicativos a Teams ou canais.
* Os usuários convidados podem acessar o conteúdo exposto em Teams ou canais.

Você pode escolher entre escopo pessoal e escopo de equipe ou canal para seu aplicativo, dependendo do seguinte:

* Para escopo pessoal, faça as seguintes perguntas:
  * Há interações um-a-um com o aplicativo necessárias por privacidade ou outros motivos? Por exemplo, verificar o saldo de licença ou outras informações privadas.
  * Haverá colaboração entre usuários que talvez não tenham nenhuma Teams? Por exemplo, encontrar os próximos eventos de toda a organização em uma empresa.
  * Há alguma notificação ou mensagens personalizadas que precisarão ser enviadas a um usuário durante toda a experiência Teams aplicativo? Por exemplo, lembretes para aprovações ou registros.
* Para um escopo compartilhado (equipe, canal ou chat), faça as seguintes perguntas:
  * As informações apresentadas pelo aplicativo, na guia ou por meio de um bot, são relevantes e úteis para a maioria dos membros em uma equipe? Por exemplo, aplicativo Scrum.
  * O contexto do aplicativo pode mudar dependendo da equipe à qual ele é adicionado? Por exemplo, as tarefas do Planner são diferentes em equipes diferentes. 
  * É possível que todos os membros em uma persona que precisem colaborar fazem parte de uma única equipe? Por exemplo, agentes trabalhando em um tíquete.

Os cenários a seguir orientarão você a entender a seleção de pontos de entrada e elementos da interface do usuário que funcionam bem com Teams de aplicativo:

> [!NOTE]
> Não é uma lista exaustiva, mas ajudará você a pensar em algumas das possibilidades disponíveis para você.

## <a name="create-share-and-collaborate-on-items-in-an-external-system"></a>Criar, compartilhar e colaborar em itens em um sistema externo

App for Microsoft Teams é uma ótima maneira de interagir com seus dados e há uma variedade de pontos de integração para escolher.

* **Extensões de mensagens com comandos de pesquisa**: Pesquisar sistemas externos e compartilhar os resultados como um cartão interativo.

* **Extensões de mensagens com comandos de** ação : Coletar informações para inserir em um armazenamento de dados ou realizar pesquisas avançadas.

* **Guias**: Crie experiências da Web incorporadas para exibir, trabalhar e compartilhar dados.

* **Conectores e webhooks**: uma maneira simples de enviar dados e enviar dados do cliente Teams.

* **Módulos de tarefa**: formulários modais interativos de onde você precisa deles para coletar ou exibir informações.

## <a name="initiate-workflows-and-processes"></a>Iniciar fluxos de trabalho e processos

Às vezes, você só precisa de uma maneira rápida de iniciar um processo ou fluxo de trabalho em um sistema externo.

* **Comandos de ação de extensões de** mensagens : Disparar a partir de mensagens, permitindo que seus usuários enviem rapidamente o conteúdo de uma mensagem para seus serviços Web.

* **Módulos de tarefa**: abra-os de uma guia, um bot ou uma extensão de mensagens para coletar informações antes de iniciar um fluxo de trabalho.

* **Bots de conversação**: Interaja com seus usuários por meio de texto e rich cards.

* **Webhooks de** saída : uma boa opção para uma interação simples de ida e volta quando você não precisa criar um bot de conversação inteiro.

## <a name="send-notifications-and-alerts"></a>Enviar notificações e alertas

Envie notificações e alertas assíncronos para seus usuários em Teams. Use cartões interativos para fornecer acesso rápido a ações comumente usadas e links para informações adicionais.

* **Bots de conversa:** envie mensagens proativas para grupos, canais ou usuários individuais.

* **Conectores e webhooks de entrada**: Permitir que um canal assine para receber mensagens. Um conector permite que os usuários adaptem a assinatura com uma página de configuração.

## <a name="ask-questions-and-get-answers"></a>Fazer perguntas e obter respostas

As pessoas têm perguntas e você provavelmente tem muitas das respostas armazenadas em algum lugar. Infelizmente, geralmente é muito difícil conectar os dois.

* **Bots de conversação**: Processamento de linguagem natural, AI, aprendizado de máquina e todas as palavras-chave. Use um bot alimentado pela nuvem inteligente para conectar seus usuários às respostas de que precisam.

* **Guias**: incorporar seu portal web existente no Teams ou criar uma versão Teams específica para a funcionalidade adicionada.

## <a name="get-social"></a>Obter social

Uma plataforma de colaboração é inerentemente uma plataforma social. Deixe seu lado criativo ser gratuito e adicionar um pouco de diversão ao seu local de trabalho. Todos os usuários devem ser capazes de enviar brincadeiras, dar parabéns, obter alguns memes, enviar alguns emojis ou qualquer outra coisa que lhe assente.

## <a name="think-in-terms-of-a-single-page-app"></a>Pense em termos de um aplicativo de página única

As guias são páginas da Web incorporadas. Praticamente tudo o que você pode fazer em um SPA, você pode fazer em uma guia em Teams. Apenas certifique-se de prestar atenção ao escopo. Guias de grupo e canal são para experiências compartilhadas e guias pessoais são para experiências pessoais. A lista de coisas da equipe entra na guia canal e a lista de suas coisas entra na guia pessoal.

## <a name="start-small"></a>Iniciar pequeno

Não sabe por onde começar? Está se sentindo sobrecarregado com a variedade incrível de opções disponíveis para você? Você deve escolher um recurso principal do seu aplicativo e começar por lá. Depois de ter uma opinião sobre o fluxo de informações por meio dos vários contextos no Teams, é muito mais simples imaginar uma interação mais complexa.

## <a name="put-it-all-together"></a>Colocar tudo junto

Dito isso, os melhores aplicativos geralmente combinam vários recursos, criando um aplicativo que envolve os usuários no contexto certo com a funcionalidade certa no momento certo. Você não deve forçar qualquer funcionalidade em um local que não pertence. Só porque você tem um bom bot de conversa um para um não significa adicioná-lo a qualquer equipe. Pontos de extensibilidade diferentes são bons para coisas diferentes, reproduzindo seus pontos fortes para criar um aplicativo bem-sucedido.

## <a name="see-also"></a>Confira também

[Crie aplicativos para o Microsoft Teams](../../overview.md)
