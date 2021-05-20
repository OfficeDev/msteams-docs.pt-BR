---
title: Mapeie seus casos de uso para Teams recursos de aplicativos
author: clearab
description: Identifique como os casos de uso do seu aplicativo podem funcionar dentro da experiência Teams.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 179d0a37d72577c36f2cc44a11a8217cb9f016b2
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566107"
---
# <a name="map-your-use-cases-to-teams-app-capabilities"></a>Mapeie seus casos de uso para Teams recursos de aplicativos

Depois de identificar *quem* é o usuário e *qual* problema você vai resolver, é hora de decidir *como* resolver o problema. A *OMS*, *o que*, e *como* completa o processo de compreensão e mapeamento de seus casos de uso para Teams recursos do aplicativo. Você precisa definir o escopo do aplicativo com base nas respostas recebidas do usuário às suas consultas e, em seguida, decidir qual recurso é mais adequado para construir seu aplicativo.

> [!NOTE]
> Você deve ter uma boa compreensão dos pontos de [entrada e elementos de interface](../../concepts/extensibility-points.md) do usuário disponíveis para o seu aplicativo. Você também deve ter certeza de que [considerou seus casos de uso](../../concepts/design/understand-use-cases.md) cuidadosamente.

## <a name="choose-the-correct-scope-for-your-app"></a>Escolha o escopo correto para o seu aplicativo

Ao escolher o escopo do aplicativo, considere o seguinte:

* Um aplicativo pode existir em todos os escopos.
* Os recursos do aplicativo, como extensões de mensagens, seguem os usuários através de escopos.
* Os usuários muitas vezes hesitam em adicionar aplicativos a Teams ou canais.
* Os usuários convidados podem acessar conteúdo exposto em Teams ou canais.

Você pode escolher entre escopo pessoal e escopo de equipe ou canal para o seu aplicativo, dependendo do seguinte:

* Para obter escopo pessoal, faça as seguintes perguntas:
  * Há interações um-a-um com o aplicativo necessários para privacidade ou outros motivos? Por exemplo, verificar o saldo de licenças ou outras informações privadas.
  * Haverá colaboração entre usuários que podem não ter nenhum Teams comum? Por exemplo, encontrar eventos de grande porte de organização em uma empresa.
  * Há alguma notificação personalizada ou mensagens que precisarão ser enviadas a um usuário durante todo o Teams experiência do aplicativo? Por exemplo, lembretes para aprovações ou registros.
* Para obter um escopo compartilhado (equipe, canal ou chat), faça as seguintes perguntas:
  * As informações apresentadas pelo aplicativo, seja na guia ou através de um bot, são relevantes e úteis para a maioria dos membros em uma Equipe? Por exemplo, aplicativo Scrum.
  * O contexto do aplicativo pode mudar dependendo da equipe em que ele é adicionado? Por exemplo, as tarefas do Planner são diferentes em equipes diferentes. 
  * É possível que todos os membros em uma persona que precisam colaborar fazem parte de uma única equipe? Por exemplo, agentes trabalhando em um bilhete.

Os seguintes cenários irão guiá-lo na compreensão da seleção de pontos de entrada e elementos de interface do usuário que funcionam bem com Teams recursos do aplicativo:

> [!NOTE]
> Não é uma lista exaustiva, mas vai ajudá-lo a pensar em algumas das possibilidades disponíveis para você.

## <a name="create-share-and-collaborate-on-items-in-an-external-system"></a>Criar, compartilhar e colaborar em itens em um sistema externo

App for Microsoft Teams é uma ótima maneira de interagir com seus dados e há uma variedade de pontos de integração para escolher.

* **Extensões de mensagens com comandos de pesquisa**: Pesquise sistemas externos e compartilhe os resultados como um cartão interativo.

* **Extensões de mensagens com comandos de ação**: Coletar informações para inserir em um armazenamento de dados ou realizar pesquisas avançadas.

* **Guias**: Crie experiências da Web incorporadas para visualizar, trabalhar e compartilhar dados.

* **Conectores e webhooks**: Uma maneira simples de empurrar dados e enviar dados para fora do Teams cliente.

* **Módulos de** tarefa : Formulários modais interativos de onde você precisar para coletar ou exibir informações.

## <a name="initiate-workflows-and-processes"></a>Iniciar fluxos de trabalho e processos

Às vezes você só precisa de uma maneira rápida de iniciar um processo ou fluxo de trabalho em um sistema externo.

* **Comandos de ação de extensões** de mensagens : Acionar as mensagens, permitindo que seus usuários enviem rapidamente o conteúdo de uma mensagem para seus serviços web.

* **Módulos** de tarefa : Abra-os a partir de uma guia, um bot ou uma extensão de mensagens para coletar informações antes de iniciar um fluxo de trabalho.

* **Bots de conversação**: Interaja com seus usuários através de cartões de texto e ricos.

* **Webhooks de saída**: Uma boa escolha para uma simples interação de ida e volta quando você não precisa construir um bot de conversação inteiro.

## <a name="send-notifications-and-alerts"></a>Enviar notificações e alertas

Envie notificações e alertas assíncronsos aos seus usuários em Teams. Use cartões interativos para fornecer acesso rápido a ações e links comumente usados para informações adicionais.

* **Bots de conversação**: Envie mensagens proativas para grupos, canais ou usuários individuais.

* **Conectores e webhooks de entrada**: Permita que um canal se inscreva para receber mensagens. Um conector permite que os usuários adaptem a assinatura com uma página de configuração.

## <a name="ask-questions-and-get-answers"></a>Faça perguntas e obtenha respostas

As pessoas têm perguntas e você provavelmente tem um monte de respostas armazenadas em algum lugar. Infelizmente, muitas vezes é muito difícil conectar os dois.

* **Bots de conversação**: Processamento de linguagem natural, IA, aprendizado de máquina e todos os buzzwords. Use um bot alimentado pela nuvem inteligente para conectar seus usuários às respostas de que precisam.

* **Guias**: Incorpore seu portal web existente em Teams ou crie uma versão específica de Teams para adicionar funcionalidade.

## <a name="get-social"></a>Obter social

Uma plataforma de colaboração é inerentemente uma plataforma social. Deixe seu lado criativo ser livre e adicione um pouco de diversão em seu local de trabalho. Todos os usuários devem ser capazes de enviar piadas, dar elogios, obter alguns memes, jogar fora alguns emojis, ou qualquer outra coisa que atinja sua fantasia.

## <a name="think-in-terms-of-a-single-page-app"></a>Pense em termos de um aplicativo de uma única página

As guias são páginas da Web incorporadas. Praticamente qualquer coisa que você pode fazer em um SPA, você pode fazer em uma guia em Teams. Apenas não se esqueça de prestar atenção ao escopo. As guias de grupo e canais são para experiências compartilhadas e guias pessoais são para experiências pessoais. A lista de coisas da equipe vai para a guia do canal e a lista de suas coisas vai para a guia pessoal.

## <a name="start-small"></a>Comece pequeno

Não sabe por onde começar? Sentindo-se um pouco sobrecarregado com a incrível variedade de opções disponíveis para você? Você deve escolher um recurso principal do seu aplicativo e começar por lá. Depois de ter uma noção do fluxo de informações através dos diversos contextos Teams, é muito mais simples imaginar uma interação mais complexa.

## <a name="put-it-all-together"></a>Coloque tudo junto

Dito isto, os melhores aplicativos geralmente combinam vários recursos, criando um aplicativo que engaja os usuários no contexto certo com a funcionalidade certa no momento certo. Você não deve forçar qualquer funcionalidade em um lugar que não pertence. Só porque você tem um bom bot de conversação um-para-um não significa que você adicioná-lo a qualquer equipe. Diferentes pontos de extensibilidade são bons para coisas diferentes, joguem com seus pontos fortes para criar um aplicativo de sucesso.

## <a name="see-also"></a>Confira também

[Crie aplicativos para o Microsoft Teams](../../overview.md)
