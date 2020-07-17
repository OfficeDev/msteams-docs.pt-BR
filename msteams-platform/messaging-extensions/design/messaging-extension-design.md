---
title: Diretrizes de design para extensões de mensagens
description: Descreve as diretrizes para a criação de extensões de mensagens
keywords: Diretrizes de design de equipes referência de dicas de extensões de mensagens recomendadas
author: EmilyyC
ms.author: qinch
ms.openlocfilehash: 5d62646c5757f93cc4f6ae6e089ef3a0918f9eea
ms.sourcegitcommit: 81ac2a1070d16e20ae0e4cb6137dce09b31914af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2020
ms.locfileid: "45152683"
---
# <a name="start-sharing-with-powerful-messaging-extensions"></a>Iniciar compartilhamento com poderosas extensões de mensagens

As extensões de mensagens são projetadas para compartilhar conteúdo acionável. Este recurso representa o maior retorno sobre o investimento (ROI) em nossa pilha. As extensões de mensagens funcionam em chat e canais, dão suporte a vários pontos de extremidade de consulta, habilitar a criação de novas entidades e trabalhar com o link Unfurling para criar visualizações de link personalizadas. O desafio é que, enquanto o recurso é poderoso e incrivelmente útil, ele não é facilmente detectável. Este guia ajudará você a criar extensões de mensagens que são prontamente encontradas e utilizadas por mais usuários.

## <a name="design-guidelines"></a>Diretrizes de design

### <a name="show-content-as-a-user-type"></a>Mostrar conteúdo como tipo de usuário

As extensões de mensagens apresentam uma maneira exclusiva de usar as pesquisas de palavras-chave para localizar conteúdo acionável que possa ser compartilhado com um ou mais usuários. Essa interação preferida permite que os usuários insiram termos de pesquisa com uma consulta automática atrasada como o tipo de usuário. Esse modelo faz um bom trabalho de simular resultados sugeridos e exige que os usuários digitem caracteres mínimos.

> [!TIP]
>É possível, mas não desejável, exigir que os usuários selecionem `enter` ou `search` antes de enviar consultas. Embora haja menos sobrecarga no serviço de back-end, esse modelo não é a norma e pode confundir os usuários.

### <a name="consider-zero-term-queries"></a>Considere consultas de prazo zero

Consultas de zero prazo são acionadas diretamente por ação do usuário, e não pelos termos de gravação do usuário em uma caixa de pesquisa. Todas as extensões de mensagens beneficiam de consultas de zero prazos, geralmente com base no que o usuário viu no serviço pela última vez. A vantagem é que a possibilidade de querer compartilhar algo que o usuário viu pela última vez é muito alta. Outras consultas de zero prazo podem ser baseadas no serviço. Por exemplo, `news` pode mostrar extensões de notícias postadas recentemente de eventos recentes e futuros.

<img width="450px" title="Nova guia de configuração" src="../../assets/images/messaging-extension/zero-term-query.png" />

### <a name="include-link-unfurling"></a>Incluir link Unfurling

Uma das maneiras mais comuns de compartilhar conteúdo no Microsoft Teams é por meio de um hiperlink, seja ela uma tarefa em que você está trabalhando ou um vídeo que encontrou engraçado. Quando um usuário compartilha um link no Teams, uma visualização incluindo imagem, título ou descrição é exibida. Com [link Unfurling](../how-to/link-unfurling.md) agora você pode personalizar essas visualizações. Os usuários também serão solicitados a instalar seu aplicativo depois de decidirem usar sua versão prévia. A adição da funcionalidade de link Unfurling ao seu aplicativo pode aumentar muito a capacidade de descoberta do aplicativo.

### <a name="highlight-your-messaging-extension"></a>Realçar sua extensão de mensagens

As extensões de mensagens nem sempre são fáceis de encontrar. Inclua capturas de tela de aplicativo na página de detalhes do aplicativo e na documentação de ajuda para requerer sua extensão de mensagens. Você também pode incluir documentação de *instruções* para sua extensão de mensagens em Tours de bot para realçar todo o aplicativo além das interações de bot.

### <a name="add-actions-on-card"></a>Adicionar ações no cartão

Não basta exibir texto para os usuários. Tem algo com que eles podem interagir e executar a próxima ação. Por exemplo, o aplicativo locais não insere um mapa no cartão, mas também tem um botão que, quando selecionado, mostrará instruções para o local. Os usuários podem executar mais tarefas depois de obter o cartão.

<img width="450px" title="Nova guia de configuração" src="../../assets/images/messaging-extension/action-on-card.png" />

### <a name="keep-users-in-the-app-context"></a>Manter os usuários no contexto do aplicativo

Se um cartão não for suficiente e você precisar fornecer um link para obter mais informações, considere abrir uma guia em vez de abrir um navegador para uma melhor experiência do usuário. *Consulte* [estender seu aplicativo do Microsoft Teams com uma guia personalizada](../../tabs/how-to/add-tab.md)
