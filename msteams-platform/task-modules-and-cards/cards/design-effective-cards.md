---
title: Criando cartões eficazes
description: Descreve as diretrizes de design para criar cartões
keywords: Diretrizes de design de equipes referência de cartões de estrutura de referência leve
ms.openlocfilehash: 33ee0b59a3a5a1490d6e2106f8532094ed852598
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672893"
---
# <a name="designing-effective-cards"></a>Criando cartões eficazes

Os cartões são trechos acionáveis do conteúdo que você pode adicionar a uma conversa através de um bot, um conector ou um aplicativo. Usando texto, elementos gráficos e botões, os cartões permitem que você se comunique com uma audiência.

Nossa estrutura de cartão elimina o ônus de projetar um UX totalmente funcional. Desenvolvemos vários tipos de cartões padrão e cada um cabe em nossas plataformas suportadas. Isso significa que o layout está totalmente encaredo e você não precisará desenvolver iterações de cartão diferentes entre plataformas. Em vez disso, você pode se concentrar na discagem em seu conteúdo.

---

## <a name="guidelines"></a>Diretrizes

Considere um cartão como uma resposta a uma pergunta de usuário ou uma configuração. Um cartão pode responder a uma pergunta direta (como "quantos erros abertos eu tenho?") ou a uma condição (como "Enviar uma lista de meus bugs abertos às 9 AM todos os dias").

> [!TIP]
> O uso de um dos nossos tipos de cartão padrão significa que você já saberá que todas as suas respostas serão bem processadas em todas as plataformas suportadas.

Um cartão pode incluir qualquer um dos seguintes elementos:<br />

[!include[Card anatomy](~/includes/design/card-image-anatomy.html)]

1. **Texto do envelope**: melhor usado para mensagens de chat. Por exemplo, se você deseja que um bot diga: "aqui está o que eu encontrei!" ou "hora do seu resumo de notícias do 1:00", essa mensagem é melhor exibida no texto do envelope.

   O texto do envelope é uma ótima maneira de injetar uma pequena personalidade no seu serviço, apenas se lembre de mantê-lo relativamente curto.

2. **Título**: seu título sempre será o maior texto no seu cartão. Ele também serve como seu "gancho", portanto, tente manter o título curto, fácil de lembrar e fácil de digitalizar.

3. **Subtítulo**: melhor usado para atribuição, mote ou como uma diretiva secundária. Este componente aparece logo abaixo do título.

4. **Image**: as imagens são dimensionadas de acordo com o contêiner. Os cartões herói têm uma largura máxima de 420px, as miniaturas têm uma largura máxima de 100px e os modos de exibição de lista só permitem o medianiz 32px no modo de área de trabalho.

5. **Texto**: melhor usado para texto sem formatação no corpo do cartão. O tamanho máximo depende do tipo de cartão que você selecionou.

6. **Botões**: melhor usado para abrir páginas da Web, guias ou conteúdo de chat adicional. Certifique-se de manter o texto do botão curto e para o ponto.

   Você pode incluir até 6 botões por cartão, mas seria recomendável seguir uma filosofia ' menos mais ' aqui.

7. **Região de toque**: esta é a região de clique do cartão. A maioria dos usuários desejará clicar em imagens automaticamente, portanto, experimente e crie seu texto para que eles saibam onde devem tocar ou clicar.

> [!TIP]
> Não é necessário incluir todos os elementos em cada cartão que você criar. Permitir que o conteúdo dite seus elementos.

---

## <a name="types-of-cards"></a>Tipos de cartões

### <a name="hero"></a>Destaque

Nosso maior cartão. Melhor usado para artigos, descrições longas ou cenários em que a imagem está informando a maior parte da história.

[!include[Card anatomy](~/includes/design/card-image-hero.html)]

### <a name="thumbnail"></a>Thumbnail

Curta e doce. Esses cartões são ideais para respostas curtas ou se você deseja retornar vários cartões de uma só vez, para que o usuário possa escolher entre várias opções. Acreditamos que essas são uma ótima maneira de vincular detalhadamente a outra guia ou serviço Web.

[!include[Card anatomy](~/includes/design/card-image-thumbnail.html)]

### <a name="sign-in"></a>Entrar

Alguns serviços exigem que os usuários entrem de forma independente da nossa autenticação. Nesse caso, você apresentaria um cartão de conexão antes que o usuário possa se conectar ao seu serviço.

[!include[Card anatomy](~/includes/design/card-image-signin.html)]

> [!TIP]
> Limitar as ocorrências de um cartão de entrada adicional, uma vez que elas representam uma considerável bomba de velocidade para novos usuários.

---

## <a name="card-collections"></a>Coleções de cartões

Também temos tipos de cartões padrão que são mais usados quando você deseja apresentar vários pedaços de conteúdo de uma só vez ou em uma sucessão rápida. Para essa finalidade, temos um carrossel, um resumo, uma lista e o que chamamos de uma ' mesclagem em bolha '.

### <a name="carousel"></a>Carrossel

Melhor usado para artigos, compras e navegação através de cartões.

[!include[Card anatomy](~/includes/design/card-image-carousel.html)]

> [!TIP]
> O carrossel será a altura máxima do seu maior cartão. Recomendamos o uso do mesmo tipo de cartão e campos de conteúdo no todo.

### <a name="digest"></a>Digest

Melhor usado para notícias, resumos e sempre que você deseja que o usuário exiba vários cartões de uma só vez. Recomendamos o uso de cartões de miniatura para resumos.

[!include[Card anatomy](~/includes/design/card-image-digest.html)]

### <a name="lists"></a>Listas

As listas são uma ótima maneira de apresentar um conjunto de objetos que podem ser varridos em um cenário "escolha um destes". As listas são melhores usadas para itens que não precisam de muita explicação.

[!include[Card anatomy](~/includes/design/card-image-list.html)]

### <a name="bubble-merge"></a>Mesclagem em bolha

Alguns efeitos interessantes podem ser obtidos enviando um herói e várias miniaturas em uma sucessão rápida. Recomendamos essa abordagem quando você quiser atender um resultado principal, mas incluir alguns itens relacionados.

[!include[Card anatomy](~/includes/design/card-image-bubble-merge.html)]

---

## <a name="best-practices"></a>Práticas recomendadas

### <a name="keep-the-noise-down"></a>Mantenha o ruído pressionado

É fácil enviar vários cartões para uma conversa, mas depois que os cartões saem do modo de exibição, eles se tornam menos úteis. Tente se limitar ao Essentials. Isso se aplica especialmente em um canal em que os usuários têm menos tolerância para o que eles percebem como "ruído".

### <a name="test-on-mobile"></a>Testar em dispositivos móveis

Os ambientes móveis são restritos por espaço e largura de banda, portanto, tenha cuidado ao incluir imagens de tamanho excessivo e conjuntos de dados grandes em listas e carrossel. Além disso, as larguras de título e os comprimentos de texto ficarão truncados em dispositivos móveis, portanto, outra coisa para ficar atento.

### <a name="check-your-graphics"></a>Verifique seus elementos gráficos

Os elementos gráficos serão dimensionados e, portanto, não se esqueça de visualizá-los em todas as plataformas.

### <a name="avoid-including-text-in-a-graphic"></a>Evitar incluir texto em um gráfico

Tudo o que precisa ser lido por um usuário deve ser incluído em um campo de texto. Após a escala dinâmica de uma imagem, qualquer texto que você adicionar a um gráfico poderá se tornar ininteligível.

### <a name="use-mentions-if-you-want-the-attention-of-specific-users"></a>Use menção se quiser a atenção de usuários específicos

> [!NOTE]
> Mencione o suporte nos cartões atualmente é suportado apenas na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md) .

As mencionas são uma ótima maneira de notificar usuários específicos em uma equipe ou em um chat de grupo. Você pode incluir um cartão em cenários, como uma tarefa atribuída a um usuário ou fornecer Parabéns a uma equipe. Saiba como incluir mençãos em cartões na página de [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). 
