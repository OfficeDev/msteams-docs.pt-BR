---
title: Mapear seus casos de uso para os recursos do aplicativo
author: clearab
description: Decidir como distribuir seu aplicativo
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 5ebfa73df9b4f2c83533a33fbc6366c2c0ccffb4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672779"
---
# <a name="map-your-use-cases-to-teams-app-capabilities"></a>Mapear seus casos de uso para recursos de aplicativos do teams

Se você ainda não tiver feito isso, certifique-se [de que os casos de uso foram considerados](~/concepts/design/map-use-cases.md) com cuidado. Você também deve ter uma boa compreensão dos [pontos de extensibilidade e dos elementos da interface do usuário](~/concepts/extensibility-points.md) disponíveis para seu aplicativo. Depois de descobrir *o que* você está tentando resolver e *quem* você está resolvendo, é hora de começar a pensar sobre *como*.

Abaixo você encontrará alguns cenários comuns e uma seleção de pontos de extensibilidade e elementos de interface do usuário que funcionam bem com eles. Não se trata de uma lista exaustiva, apenas para ajudá-lo a pensar em algumas das possibilidades disponíveis para você e a plataforma do Microsoft Teams.

## <a name="create-share-and-collaborate-on-items-in-an-external-system"></a>Criar, compartilhar e colaborar em itens em um sistema externo

O aplicativo para o Microsoft Teams é uma ótima maneira de interagir com seus dados, e há uma variedade de pontos de integração para escolher.

* Extensões de mensagens com comandos de pesquisa – pesquise sistemas externos e compartilhe os resultados como um cartão interativo.

* Extensões de mensagens com comandos de ação-coletar informações para inserir em um repositório de dados ou executar pesquisas avançadas.

* Guias: criar experiências da Web incorporadas para exibir, trabalhar e compartilhar dados.

* Conectores e WebHooks-uma maneira simples de enviar dados para e enviar dados do cliente do teams.

* Módulos de tarefas-formulários modais interativos de onde você precisar coletar ou exibir informações.

## <a name="initiate-workflows-and-processes"></a>Iniciar fluxos de trabalho e processos

Às vezes, você precisa apenas de uma maneira rápida de iniciar um processo ou fluxo de trabalho em um sistema externo.

* Comandos de ação de extensões de mensagens-disparar de mensagens, permitindo que os usuários enviem rapidamente o conteúdo de uma mensagem para seus serviços Web.

* Módulos de tarefas: Abra-os a partir de uma guia, de um bot ou de uma extensão de mensagens para coletar informações antes de iniciar um fluxo de trabalho.

* Bots de conversa-interaja com seus usuários por meio de texto e cartões ricos.

* WebHooks de saída-uma boa opção para uma simples interação de frente e para trás quando você não precisa criar um bot de conversa inteiro.

## <a name="send-notifications-and-alerts"></a>Enviar notificações e alertas

Envie notificações e alertas assíncronos para seus usuários no Microsoft Teams. Use cartões interativos para fornecer acesso rápido a ações comumente usadas e links para informações adicionais.

* Bots de conversa-envie mensagens pró-ativas para grupos, canais ou usuários individuais.

* Conectores & WebHooks de entrada: permitir que um canal assine receber mensagens. Com um conector permite que os usuários personalizem a assinatura com uma página de configuração.

## <a name="ask-questions-and-get-answers"></a>Fazer perguntas e obter respostas

Pessoas têm dúvidas. Você provavelmente tem muitas das respostas armazenadas em algum lugar. Infelizmente, o que costuma ser muito difícil de conectar os dois juntos.

* Bots de conversa-processamento de linguagem natural, AI, aprendizado de máquina, todos os buzzwords. Use um bot alimentado pela nuvem inteligente para conectar seus usuários às respostas de que precisam.

* Guias-incorpore o portal da Web existente no Microsoft Teams ou crie uma versão específica do teams para funcionalidade adicional.

## <a name="get-social"></a>Obter social

Uma plataforma de colaboração é inerentemente uma plataforma social. Deixe que seu lado criativo fique livre e adicione uma diversão ao seu ambiente de trabalho.

* Todos eles-enviam piadas, dão Parabéns, obtêm alguns memess, emitem alguns emojis ou qualquer outra coisa que tenha sido elaborado.

## <a name="anything-you-can-do-in-a-single-page-app-spa"></a>Tudo o que você pode fazer em um aplicativo de página única (SPA)

As guias são páginas da Web incorporadas. Praticamente tudo o que você pode fazer em um SPA, você pode fazer em uma guia no Teams. Só não se esqueça de prestar atenção às guias de grupo e canal de escopo para experiências compartilhadas, guias pessoais são para... experiências pessoais. A lista de itens da equipe fica na guia canal, a lista de suas coisas é exibida na guia pessoal.

## <a name="start-small"></a>Iniciar pequeno

Não sabe por onde começar? Você se sente um pouco sobrecarregado com a variedade de opções incríveis disponíveis? Não fret, escolha um recurso principal do seu aplicativo e inicie lá. Depois que você se sentir para o fluxo de informações através dos vários contextos no Teams, será muito mais simples fazer uma interação mais complexa.

## <a name="putting-it-all-together"></a>Colocando tudo em um só lugar

Dito isso, os melhores aplicativos geralmente combinam vários recursos, criando um aplicativo que contrata usuários no contexto certo com a funcionalidade correta no momento certo. Não tente forçar a funcionalidade em um local que não pertença-apenas porque você tem um bom bot de conversa um-para-um não significa que você deve apenas adicioná-lo a uma equipe. Pontos de extensibilidade diferentes são bons para coisas diferentes; Jogue até seus pontos fortes e seu aplicativo brilhará.
