---
title: Diretrizes de design para bots
description: Descreve as diretrizes para a criação de bots
keywords: Diretrizes de design de equipes referência de bots
ms.openlocfilehash: 731e36ac3437e22435ea6054ad359d0c6bc2ead3
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2020
ms.locfileid: "44453886"
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

### <a name="onboarding-users"></a>Usuários de integração

É fundamental que os bots se apresentem e transmitam o que eles podem fazer aos usuários. Esse *valor o Exchange* ajuda os usuários a entender o que fazer com o bot, onde as limitações podem estar, e o mais importante, ajuda os usuários a tolerar a interação com uma máquina que não será tão intuitiva como uma pessoa real. Além disso, ele concede permissão aos dados do usuário no Exchange para o valor real que o serviço fornece.

#### <a name="welcome-messages"></a>Mensagens de boas-vindas

As mensagens de boas-vindas são a melhor maneira de definir o tom do bot e devem ser usadas em cenários pessoais e de equipe ou grupo. A mensagem informa o que o bot faz e algumas maneiras comuns de interagir com ele. Use exemplos de recursos específicos, como "*Tente perguntar...*" em uma lista com marcadores. Sempre que possível, essas sugestões devem retornar respostas armazenadas. É fundamental que os exemplos de recursos funcionem sem exigir que os usuários entrem.

#### <a name="tours"></a>Viagens

Inclua um atributo *Take a Tour* com mensagens de boas-vindas e respostas para entrada de usuário equivalente a "*ajuda*". Essa é a maneira mais eficaz de permitir que os usuários saibam o que um bot pode fazer. Os carrossel em experiências de um-para-um são uma maneira excelente de informar essa história e incluir os botões de *experimentar que* os links para exemplos de respostas possíveis sejam incentivados. Os Tours também são bons lugares para falar sobre outros recursos do aplicativo. Por exemplo, você pode incluir capturas de tela das guias de extensões de mensagens e equipes.  Os usuários não devem ter que entrar no Access e usar um tour.

Quando os Tours são usados em cenários de equipe ou grupo, eles devem ser abertos em um módulo de tarefa para não adicionar mais ruído de cartão às conversas em andamento entre usuários.

### <a name="responding-to-users-and-failing-gracefully"></a>Responder aos usuários e falhar normalmente

Seu bot também deve ser capaz de responder a coisas como "*Hi*", "*Help*" e "*thanks*" ao assumir erros comuns e coloquialismos em conta. Por exemplo:

#### <a name="x2713-hello"></a>&#x2713; Hello

`"Hi"`  `"How are you"`  `"Howdy"`

#### <a name="x2713-help"></a>&#x2713; ajuda

`"What do you do?"`  `"How does this work?"`  `"What the heck?"`

#### <a name="x2713-thanks"></a>&#x2713; agradecimentos

`"Thank you"`  `"Thankyou"`  `"Thx"`

O bot deve ser capaz de lidar com os seguintes tipos de consultas e entradas:

> [!div class="checklist"]
>
> * **Perguntas reconhecidas**. Essas são as perguntas de "cenário de melhor caso" que você espera dos usuários.
> * **Não há perguntas reconhecidas**. Consultas sobre funcionalidades não suportadas e/ou entradas aleatórias, não relacionadas ou impróprias.
> * **Perguntas não reconhecidas**: entrada ou entradas que são ininteligível, sem significado ou sem sentido.

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

Em conversas pessoais entre um bot e uma única pessoa, as guias podem conter informações e listas específicas do usuário. Eles também são um bom local para manter respostas de bot para perguntas frequentes (FAQs), de modo que os usuários não precisem continuar fazendo isso.

### <a name="x2713-a-place-to-finish-a-conversation"></a>&#x2713; um local para concluir uma conversa

Você pode vincular a uma guia de um cartão. Se o seu bot fornecer uma resposta que exija algumas etapas adicionais, ele pode vincular a uma guia para concluir a tarefa ou o fluxo. Por exemplo, em resposta a, "como faço para formatar meu iPhone?", uma boa resposta pode ser um cartão que descreve as primeiras etapas e tem um botão para *Mostrar mais* que, em seguida, leva o usuário à guia de *ajuda* do bot e vincula detalhadamente as instruções específicas.

### <a name="x2713-a-place-to-host-a-settings-page"></a>&#x2713; um local para hospedar uma página de configurações

Os bots devem ter um controle de usuário. Para muitos bots, ele é permitido por meio de uma interface de chat; no entanto, é difícil lembrar-se dessas configurações. Uma guia Configurações pode exibir configurações de usuários, permitir que os usuários alterem todos de uma vez e também podem ser um bom ponto de indisponibilidade para comportamentos personalizados de bot mais complexos.

### <a name="x2713-a-place-to-provide-some-help"></a>&#x2713; um local para fornecer ajuda

Adicione uma guia que instrua os usuários sobre como se comunicar com o bot. Você pode fornecer um contexto para o que ele faz ou perguntas frequentes.

![Fornecer ajuda](~/assets/images/framework/framework_bots_tbot-help.png)

> [!TIP]
> A incorporação de partes do seu site em uma guia ajudará os usuários a manter o contexto de uma conversa quando usarem o serviço. Ele remove a necessidade de iniciar o serviço em um navegador e alternar entre aplicativos.

---

## <a name="bots-in-channels"></a>Bots em canais

Chamar um bot em um canal pode ser realizado por `@mention` . A caixa de diálogo de bot deve ser exclusiva em canais e grupos vs. cenários um-para-um e, geralmente, é uma boa ideia considerar abordagens distintas. Isso se aplica especialmente nos seguintes casos:

### <a name="sensitive-data-sent-by-a-bot"></a>Dados confidenciais enviados por um bot

Embora os usuários de uma equipe possam ser conhecidos do serviço, as funções de usuário reais não podem. Isso significa que, por exemplo, em um cenário de educação que envolve o anti-intimidação, as informações de contato do pai e do aluno não serão compartilhadas em uma configuração de equipe. Em vez disso, a mensagem do bot pode ser: "dois incidentes anti-intimidação ocorridos hoje", junto com um botão para mostrar detalhes.

Os detalhes de inicialização em uma página da Web ou um módulo de tarefa podem solicitar credenciais de usuário ou consultas em um índice para funções de usuário emparelhadas com contas AAD. Em ambas as opções, os dados estão em um escopo de exibição particular e não haverá perda de dados. Se os mesmos dados são enviados em um chat de um para um entre um usuário e o bot, os dados são visíveis apenas para o usuário naquele contexto e, portanto, é seguro para exibir totalmente na mensagem do bot. O uso de usuários de um canal para um chat de um-para-um deve ser evitado, no entanto, como a navegação forçada é altamente interrompida.

### <a name="sending-cards-as-a-response-to-interactions"></a>Enviando cartões como uma resposta a interações

Enquanto o envio de um cartão de carrossel em resposta para *fazer um tour* em um chat de um-para-um é perfeitamente aceitável, o mesmo padrão pode produzir dezenas ou centenas de *carrossel de Tour* em um canal ativo com muitos usuários. Para evitar isso, os cartões secundários devem ser hospedados em um módulo de tarefa. Este padrão mantém os usuários no contexto com o canal, mantém o canal limpo de respostas excessivas de bot e, opcionalmente, pode considerar diferentes funções de usuário quando o *Tour* é mostrado.

## <a name="useful-tips"></a>Dicas úteis

### <a name="x2713-remember-bots-arent-assistants"></a>&#x2713; lembrar, os bots não são assistentes

Diferentemente de agentes, por exemplo, Cortana, bots atuam como especialistas.

### <a name="x2713-discourage-chitchat"></a>&#x2713; desencorajar Chitchat

A menos que seu bot seja criado para conversa, encontre maneiras de redirecionar Chitchat para a conclusão da tarefa.

### <a name="x2713-introduce-some-personality"></a>&#x2713; apresentar algumas personalidades

Mantenha sua personalidade de bot consistente com a voz do seu produto. Pense no bot como palestra à sua empresa.

### <a name="x2713-maintain-tone"></a>&#x2713; manter Tom

Determine se você deseja que o Tom seja amigável e claro, "apenas os fatos" ou a mais peculiaridades.

### <a name="x2713-encourage-easy-task-flow"></a>&#x2713; incentivar o fluxo de tarefas fácil

Dê suporte a interações de várias perfeitas e ainda permitindo perguntas totalmente formadas. Prever a próxima etapa ajudará os usuários a obter muito mais facilidade nos fluxos de tarefas.

Se um usuário executar várias etapas para concluir uma tarefa, permita que o bot as assuma por meio de cada etapa, mas termine por ter sugerido um caminho mais rápido. Por exemplo, se um usuário levou várias pessoas para definir uma reunião (especificando primeiro uma reunião e, em seguida, identificando com quem e, em seguida, informando a hora e, em seguida, informando o dia), conclua a conversa com a seguinte sugestão: na próxima vez, tente perguntar se você pode agendar uma reunião com Bob em 1:00 amanhã.
