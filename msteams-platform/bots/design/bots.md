---
title: Diretrizes de design para bots
description: Descreve as diretrizes para a criação de bots
keywords: Diretrizes de design de equipes referência de bots
ms.openlocfilehash: f59a1e9c280f27567692b4d10341db79d05c3464
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672868"
---
# <a name="start-talking-with-bots"></a>Começar a falar com bots

Bots são aplicativos de conversa que executam um conjunto estreito ou específico de tarefas. Eles fornecem uma oportunidade para se comunicar com os usuários, responder às suas perguntas e notificá-los proativamente sobre as alterações. Eles são uma ótima maneira de entrar.

---

## <a name="guidelines"></a>Diretrizes

### <a name="avatars"></a>Avatares

Os Avatar avatars no Teams estão moldados como hexágonos para que as pessoas possam afirmar rapidamente que estão conversando com um bot, em vez de uma pessoa. Você enviará o Avatar como um quadrado e o cortará para você. Quando se trata de avatars, recomendamos que você se torne legível de 2 metros de distância e usando um contraste maior.

[!include[Avatar image](~/includes/design/bot-avatar-image.html)]

### <a name="buttons"></a>Botões

Oferecemos suporte para até seis botões por cartão. Seja conciso ao escrever o texto do botão e lembre-se de que a maioria dos botões só deve solucionar a tarefa em mãos.

### <a name="graphics"></a>Recurso

Os gráficos são uma boa maneira de informar uma história, mas nem todas as conversas de bot exigem elementos gráficos, portanto, use-as para o máximo impacto.

### <a name="responding-to-users-and-failing-gracefully"></a>Responder aos usuários e falhar normalmente

Seu bot também deve ser capaz de responder a coisas como "Hi", "Help" e "Thanks", enquanto adota erros comuns de ortografia e coloquialismos em conta. Por exemplo:

#### <a name="x2713-hello"></a>&#x2713; Hello

`Hi` `how are you` `howdy`

#### <a name="x2713-help"></a>&#x2713; ajuda

`What do you do?` `How does this work?` `What the heck?`

#### <a name="x2713-thanks"></a>&#x2713; agradecimentos

`Thank you` `thankyou` `thx`

O bot deve ser capaz de lidar com os seguintes tipos de consultas e entradas:

* **Perguntas reconhecidas**: Estas são as perguntas de "melhor cenário" que você anteciparia dos usuários.
* **Não há perguntas reconhecidas**: consultas sobre funcionalidades sem suporte, partes aleatórias de informações ou quando alguém deseja repetir o seu bot.
* **Perguntas não reconhecidas**: entradas não inteligível (por exemplo, ininteligível).

Exemplos de personalidade de bot e tipos de resposta:

[!include[Bot responses](~/includes/design/bot-responses-table.html)]

> [!TIP]
> Ao escrever seu script de bot, pergunte-se: "minha empresa será embarrassed se uma resposta for capturada e compartilhada?"

### <a name="understanding-what-users-are-trying-to-say"></a>Noções básicas sobre o que os usuários estão tentando dizer

#### <a name="use-a-thesaurus-for-synonyms"></a>Usar um dicionário de sinônimos para sinônimos

Ao fazer o debate de variações, use um dicionário de sinônimos e obtenha às pessoas o máximo de diferentes planos de fundo possíveis para ajudá-lo a gerar diferentes interpretações de cada consulta.

#### <a name="make-use-of-telemetry-and-interviews"></a>Fazer uso de telemetria e entrevistas

Descubra o que os usuários estão dizendo e qual era a intenção de consultar seu bot. Este será um processo contínuo à medida que você obtém usuários em diferentes locais e tipos de empresas. Você pode ajustar o reconhecimento de idioma e o mapeamento de intenções com o idioma entendendo o serviço inteligente ([Luis](/azure/cognitive-services/luis/what-is-luis)).

### <a name="how-often-should-you-use-your-bot-to-reach-out-to-a-user"></a>Com que frequência você deve usar o bot para entrar em um usuário?

#### <a name="x2713-when-a-state-has-changed"></a>&#x2713; quando um estado tiver sido alterado

Por exemplo, se uma atribuição for marcada como concluída, quando um erro for alterado, quando uma nova mídia social estiver disponível ou quando uma pesquisa tiver sido concluída.

#### <a name="x2713-when-the-timing-is-right"></a>&#x2713; quando o intervalo é para a direita

Seu bot pode agir como um resumo diário, enviando uma notificação para o usuário ou canal em uma frequência específica.

Deixe o usuário no controle. Fornecer configurações de notificação que incluem frequência e prioridade.

[!include[Bot notification](~/includes/design/bot-notification-image.html)]

---

## <a name="using-tabs"></a>Usando guias

As guias tornam o bot muito mais funcional. Com guias, você pode criar o seguinte:

### <a name="x2713-a-place-to-host-standing-queries"></a>&#x2713; um local para hospedar consultas em pé

Em conversas pessoais entre um bot e uma única pessoa, as guias podem alojar informações e listas específicas do usuário. Eles também são um bom local para manter respostas de bot para perguntas frequentes (FAQs), de modo que os usuários não precisem continuar fazendo isso.

### <a name="x2713-a-place-to-finish-a-conversation"></a>&#x2713; um local para concluir uma conversa

Você pode vincular a uma guia de um cartão. Se o seu bot fornecer uma resposta que exija algumas etapas adicionais, ele pode vincular a uma guia para concluir a tarefa ou o fluxo.

### <a name="x2713-a-place-to-provide-some-help"></a>&#x2713; um local para fornecer ajuda

Adicione uma guia que instrua os usuários sobre como se comunicar com o bot. Você pode fornecer um contexto para o que ele faz ou perguntas frequentes.

![Fornecer ajuda](~/assets/images/framework/framework_bots_tbot-help.png)

> [!TIP]
> A incorporação de partes do seu site em uma guia ajudará alguém a manter o contexto de uma conversa enquanto usa o serviço. Ele remove a necessidade de iniciar o serviço em um navegador e alternar entre aplicativos.

---

## <a name="best-practices"></a>Práticas recomendadas

### <a name="x2713-bots-arent-assistants"></a>&#x2713; bots não são assistentes

Diferentemente de agentes, por exemplo, Cortana, bots atuam como especialistas.

### <a name="x2713-discourage-chitchat"></a>&#x2713; desencorajar Chitchat

A menos que seu bot seja criado para conversa, encontre maneiras de redirecionar Chitchat para a conclusão da tarefa.

### <a name="x2713-introduce-some-personality"></a>&#x2713; apresentar algumas personalidades

Mantenha sua personalidade de bot consistente com a voz do seu produto. Pense no bot como palestra à sua empresa.

### <a name="x2713-maintain-tone"></a>&#x2713; manter Tom

Determine se você deseja que o Tom seja amigável e claro, "apenas os fatos" ou a mais peculiaridades.

### <a name="x2713-encourage-easy-task-flow"></a>&#x2713; incentivar o fluxo de tarefas fácil

Dê suporte a interações de várias perfeitas e ainda permitindo perguntas totalmente formadas. Prever a próxima etapa ajudará os usuários a obter muito mais facilidade nos fluxos de tarefas.

Se um usuário executar várias etapas para concluir uma tarefa, permita que o bot as assuma por meio de cada etapa, mas termine por ter sugerido um caminho mais rápido. Por exemplo, se um usuário levou várias pessoas para definir uma reunião (especificando primeiro uma reunião e, em seguida, identificando com quem e, em seguida, informando a hora e, em seguida, informando o dia), conclua a conversa com a seguinte sugestão: na próxima vez, tente perguntar se você é possível agendar uma reunião com Bob em 1:00 amanhã.