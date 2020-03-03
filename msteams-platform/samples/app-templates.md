---
title: Modelos de aplicativo do Microsoft Teams
description: Links e descrições de modelos de aplicativos para a plataforma Microsoft Teams
keywords: Demonstração de exemplos de modelos do Microsoft Teams
ms.openlocfilehash: 36f04727828b3bfa3be9b808cafcd33c11bf2c0d
ms.sourcegitcommit: 646a8224523be7db96f9686e22d420d62d55d4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42365266"
---
# <a name="app-templates-for-microsoft-teams"></a>Modelos de aplicativos para o Microsoft Teams

Os modelos de aplicativos são aplicativos prontos para produção para o Microsoft Teams que são orientados pela Comunidade, fontes abertas e disponíveis no GitHub. Cada uma contém instruções detalhadas para implantar e instalar o aplicativo para sua organização, fornecendo um aplicativo pronto para usar que você pode instalar e começar a usar imediatamente. O código-fonte completo também está disponível, para que você possa explorá-lo em detalhes ou bifurcar o código e alterá-lo para atender às suas necessidades específicas.

## <a name="key-benefits-of-using-app-templates"></a>Principais benefícios do uso de modelos de aplicativos

* **Experiência de plug and Play:** Todos os modelos de aplicativos incluem scripts de implantação que permitirão que você hospede todos os serviços necessários no Microsoft Azure. Nenhuma codificação é necessária para implantar os aplicativos.
* **Código pronto para produção:** Os modelos de aplicativos estão de acordo com as práticas recomendadas em relação à segurança e à infraestrutura, e todas as alterações enviadas à Comunidade são revisadas para garantir a conformidade contínua.
* **Personalizável e extensível:** Embora todos os modelos de aplicativos estejam prontos para implantar como estão, fornecemos toda a base de código e scripts de implantação para que você possa facilmente personalizá-los ou estendê-los para atender às suas necessidades exclusivas.
* **Documentação detalhada & suporte:** Todos os modelos de aplicativos são acompanhados por documentação de ponta a ponta nas etapas de arquitetura, implantação e configuração da solução. Os repositórios também são monitorados, portanto, informe qualquer problema que você encontrar, gerando um problema no GitHub.

## <a name="celebrations"></a>Celebrações

Comemorações é um aplicativo do teams que ajuda os membros da equipe a se comemorarem de aniversários, datas comemorativas e outros eventos recorrentes. Ele memoriza ocasiões especiais de todos os membros da equipe e envia uma mensagem amigável em todas as equipes selecionadas no momento da criação do evento, para fazer com que os membros da equipe se sintam especiais no dia.

O aplicativo fornece uma interface fácil para que todos os membros da equipe adicionem pessoal e visualizem seus eventos, além de permitir que o usuário selecione as equipes nas quais os eventos são compartilhados.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="company-communicator"></a>Communicator da empresa

O aplicativo do Communicator da empresa permite que as equipes corporativas criem e enviem mensagens destinadas a várias equipes ou grande número de funcionários por meio de chat, permitindo que a organização atinja os funcionários com o direito de colaborar. Use este modelo para vários cenários, como novos comunicados de iniciativa, integração de funcionários, aprendizado e desenvolvimento modernos ou difusões em toda a organização.

O aplicativo fornece uma interface fácil para usuários designados para criar, Visualizar, colaborar e enviar mensagens.

Ele fornece uma base para criar recursos de comunicação direcionados personalizados, como telemetria personalizada em quantos usuários foram confirmados ou interagindo com uma mensagem.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![Perguntas frequentes mais sobre gif](~/assets/images/CompanyCommunicatorCompose.png)

## <a name="faq-plus"></a>Perguntas Frequentes Plus

A conversa Q&um bots é uma maneira fácil de fornecer respostas para perguntas frequentes dos usuários. No entanto, a maioria dos bots falha ao se envolver com usuários de forma significativa, pois não há nenhum homem no loop quando o bot falha. O bot de perguntas frequentes é um&amigável para um bot que traz um homem no loop quando não é possível ajudar. É possível fazer uma pergunta ao bot e o bot responde com uma resposta se ela estiver contida na base de dados de conhecimento. Caso contrário, o bot permite que o usuário envie uma consulta que, em seguida, é lançada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte, agindo de dentro da própria equipe.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-faqplusplus-app)

> [!NOTE]
> A versão 2020 do **perguntas frequentes mais, a versão 2,** oferece suporte a uma resolução de p&a um melhor, permitindo que a equipe de especialistas realize o seguinte:
>
> &#x2714; adicionar novos Q&diretamente à base de dados de conhecimento usando extensões de mensagem.
>
> &#x2714; editar e excluir Q&um par adicionado por um bot.
>
> &#x2714; rastrear o histórico de revisão de Q&como.
>
> &#x2714; configurar uma resposta com detalhes adicionais para exibir como um [cartão adaptável](/task-modules-and-cards/cards/cards-reference#adaptive-card).
>
>[**Obter no GitHub**](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)
>
>

![Perguntas frequentes mais sobre gif](~/assets/images/FAQPlusEndUser.gif)

## <a name="hr-support"></a>Suporte de RH

O bot de suporte de RH é um&amigável para um bot que oferece um profissional de suporte/especialista da equipe de RH no loop quando não é possível ajudar. É possível fazer uma pergunta ao bot e o bot responde com uma resposta se ela estiver contida na base de dados de conhecimento. Caso contrário, o bot permite que o usuário envie uma consulta que, em seguida, é lançada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte, agindo de dentro da própria equipe. Além disso, o bot sugere links para as políticas/perguntas de RH recomendadas pesquisando marcas pré-configuradas na pergunta. Esses blocos também podem ser encontrados na guia associada como uma referência rápida. O suporte a RH funciona bem para o QnA de peso leve e para oferecer suporte rápido ao lançar novos projetos/iniciativas na organização.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![Suporte de RH](~/assets/images/expert-user.png)

## <a name="list-search"></a>Pesquisa de lista

A colaboração no Microsoft Teams freqüentemente faz referência a informações contidas em itens em uma lista do SharePoint. Simplesmente colar um link para o item em questão obriga todos a mudar o contexto da conversa, localizar as informações necessárias e, em seguida, retornar ao Teams para continuar a conversa. Como a conversa continua normalmente, as pessoas terão que voltar para o item de referência várias vezes para verificar novos comentários e atualizar suas memórias de informações contidas no item. Essa alternância de contexto cria uma barreira para a colaboração suave e é uma receita para coisas que ocorrem por meio de rachaduras.

Para ajudar a aliviar esse problema, estamos felizes em trazer para você o modelo de aplicativo de pesquisa de lista. Milhões de usuários usam o SharePoint para alimentar alguns dos fluxos de trabalho principais em suas organizações. No entanto, colaborar em listas pode ser especialmente entediante. Usando o modelo de aplicativo de pesquisa de lista no Microsoft Teams, os usuários podem inserir informações de itens de lista do SharePoint diretamente em uma conversa de chat para aliviar a alternância de contexto causada pela simples inserção de um link em um chat. As informações são inseridas como um cartão de formatação automática fácil de ler, ajudando os usuários a se manterem envolvidos na conversa.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Listar aplicativo de pesquisa](~/assets/images/list-search-template.png)

## <a name="custom-stickers"></a>Adesivos personalizados

Autoexpressão é essencial para uma cultura de equipe íntegra. Esse modelo de aplicativo é uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) que permite que os usuários usem adesivos e gifs personalizados no Microsoft Teams. Este modelo oferece uma experiência de configuração fácil e baseada na Web, onde qualquer pessoa com acesso à configuração pode carregar os GIFs/adesivos/imagens que eles desejam que seus usuários finais tenham, permitindo que toda a equipe use qualquer conjunto de adesivos escolhido.

Este aplicativo também permite o compartilhamento fácil de imagens/GIFs/adesivos entre equipes sem precisar de acesso a sites do SharePoint ou canais individuais como mecanismos de armazenamento e compartilhamento. Por exemplo, as equipes de produto podem compartilhar facilmente imagens de produtos e GIFs para equipes de mídia social, marketing e vendas programaticamente. Um também pode estender esse aplicativo, disparando um fluxo de notificação para equipes ou pessoas específicas quando novas imagens/GIFs forem disponibilizadas.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![Aplicativo adesivo](~/assets/images/stickers.png)

## <a name="icebreaker"></a>Frases de apresentação

O Icebreaker é um [bot do Microsoft Teams](../bots/what-are-bots.md) que ajuda sua equipe a ficar mais perto ao emparelhar dois membros aleatórios da equipe a cada semana para atender. O bot torna o agendamento fácil, sugerindo automaticamente as horas livres que funcionam para ambos os membros. Fortaleça as conexões pessoais e construa uma Knit Community com esse aplicativo.

Além de encorajar as conexões pessoais em toda a sua equipe, o aplicativo do Icebreaker pode ajudar a cultivar comunidades baseadas em interesses dentro da sua organização. Por exemplo, você pode usar este aplicativo para um grupo de interesse do DevOps para ajudar as ideias e práticas recomendadas espalhadas de forma orgânica em sua organização.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Aplicativo Icebreaker](~/assets/images/icebreaker.png)

## <a name="scrum-status-bot"></a>Bot de status do Scrum

O caminho de status do Scrum é um simples bot de assistente do Scrum que permitirá que os usuários executem reuniões de reserva assíncronas e forneçam e facilite que os usuários compartilhem suas atualizações diárias. Ele foi projetado para funcionar em bate-papos de grupo do Teams e todos os membros podem contribuir para o Scrum. Um pode iniciar e finalizar um Scrum e pode exibir as atualizações feitas por outras pessoas em um Scrum em execução.

[Git It no GitHub](https://github.com/OfficeDev/microsoft-teams-app-scrumstatus/)

![Bot de status do Scrum](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="crowdsourcer-bot"></a>Bot Crowdsourcer

Crowdsourcer é um [bot do Microsoft Teams](../bots/what-are-bots.md) que fornece às equipes consultadas informações que foram originadas de forma colaborativa de membros do grupo. É uma ótima maneira de responder às perguntas frequentes, permitindo que os participantes entrem em contato ativamente e contribuam para um recurso de informações divertido e útil.

[Obter no github](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Desuma interação do usuário final da torcida](../assets/images/crowdsourcer.png)

## <a name="expert-finder-bot"></a>Bot do localizador expert

O expert Finder é um [bot do Microsoft Teams](../bots/what-are-bots.md) que identifica membros específicos da organização com base em seus respectivos atributos de qualificações, interesses e educação. Membros encontrem especialistas em uma organização que correspondam a uma pesquisa de palavra-chave dos perfis de usuário do Azure Active Directory.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demonstração dos resultados da pesquisa do Expert Finder](../assets/images/expert-finder.png)

## <a name="book-a-room-bot"></a>Bot de livro a sala

Book-a-Room é um [bot do Microsoft Teams](../bots/what-are-bots.md) que permite que os usuários encontrem e reservem rapidamente uma sala de reunião para 30 (padrão), 60 ou 90 minutos a partir da hora atual. Os escopos de bot de livro-a-Room para conversas pessoais ou de 1:1.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom)

![Demonstração de livro a sala](../assets/images/book-a-room.png)

## <a name="attendance-app"></a>Aplicativo de presença

O aplicativo de presença é uma guia [aplicativos de energia](https://docs.microsoft.com/powerapps/maker/canvas-apps/embed-teams-appdesigned) que pode ser fixado em uma equipe. Ele foi projetado para registrar a presença, geralmente em configurações como ambientes de aprendizado e treinamento. Os usuários podem marcar ou editar a presença de até 30 dias no passado e exibir os relatórios de presença resumidos para um grupo inteiro ou participantes individuais.

[Obter no GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance)

![Demonstração do aplicativo de presença](../assets/images/attendance-app.png)

Tem uma ideia para um modelo de aplicativo que você gostaria de ver? [Informe-nos](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).
