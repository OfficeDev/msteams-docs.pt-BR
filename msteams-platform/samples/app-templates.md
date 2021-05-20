---
title: modelos de aplicativos Microsoft Teams
description: Links e descrições de modelos de aplicativos para a plataforma Microsoft Teams
ms.topic: reference
keywords: Microsoft Teams modelos amostras demonstram demonstração
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: 8cfb066ee3c202fb8611a61bbde3058207a62a35
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566237"
---
# <a name="app-templates-for-microsoft-teams"></a>Modelos de aplicativos para o Teams

Modelos de aplicativos são exemplos de aplicativos completos para Microsoft Teams que são de código aberto e estão disponíveis em GitHub. Cada modelo de aplicativo contém instruções detalhadas para implantar e instalar esse aplicativo para sua organização. Ele também fornece um aplicativo de amostra que você pode instalar e começar a usar imediatamente. O código-fonte completo também está disponível, o que permite explorá-lo em detalhes ou bifurcar o código e alterá-lo para atender aos seus requisitos específicos.
Todos os modelos de aplicativos são fornecidos nos termos [da Licença do MIT.](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE)

> [!NOTE] 
> Você deve licenciar e apoiar aplicativos criados a partir de modelos de aplicativos para seus usuários e organizações.

**&#9734; Indica modelos de aplicativos recém-lançados.**

### <a name="key-benefits"></a>Principais benefícios

* **Implantar diretamente na nuvem:** Todos os modelos de aplicativos incluem scripts de implantação que permitem hospedar todos os serviços necessários em Microsoft Azure ou na Plataforma de Energia. 
* **Código de amostra recomendado:** Os modelos de aplicativos estão de acordo com as práticas recomendadas em torno de segurança e infraestrutura. Todas as alterações submetidas à comunidade nos modelos do aplicativo são revisadas para garantir a conformidade.
* **Personalizável e extensível:** Embora todos os modelos de aplicativos sejam implantados com configuração mínima, toda a base de código e scripts de implantação são fornecidos, para que você possa facilmente personalizá-los ou amplie-os para atender às suas necessidades exclusivas.
* **Documentação detalhada:** Todos os modelos de aplicativos são acompanhados por documentação completa sobre arquitetura de soluções, implantação e etapas de configuração.  

## <a name="adoption-bot"></a>Bot de adoção 

Adoption Bot é um bot de chat de cuidados do usuário construído com power virtual agent para Teams PVA. É considerada como a versão PVA do FAQ Plus. Adoção Bot responde mais de 100 perguntas comuns sobre Microsoft 365 e Teams. Você pode editar os tópicos existentes, adicionar seus próprios tópicos e ingerir perguntas frequentes existentes. Se os usuários precisarem de ajuda adicional, o Adoption Bot pode conectá-los a especialistas ou até mesmo ser estendido para abrir bilhetes de serviço com conectores de fluxo premium. Este bot é auto-instalado ou incorporado em um aplicativo personalizado, como o [Adoption Hub](https://github.com/akporzondek/adoption_hub).

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot)

## <a name="adoption-tool--champion-management-platform-9734"></a>Ferramenta de Adoção- Plataforma de Gestão Campeã &#9734;

O modelo de aplicativo Champion Management Platform (CMP) ajuda você a gerenciar, dimensionar e inspirar seus campeões de trabalho em equipe a conseguir mais. Este modelo de aplicativo é construído sobre o Estrutura do SharePoint e carregado em uma guia dentro de uma equipe. Os grupos podem aproveitar essa ferramenta para ajudar a gerenciar a adesão ao programa, fornecer uma tabela de classificação e tipos de eventos para registro e ferramentas para sobrepor crachás digitais aos participantes do programa.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-champion-management)

## <a name="adoption-tool--microsoft-365-learning-pathways-get-started-9734"></a>&#9734; de Caminhos de Aprendizagem Microsoft 365 (Introdução Microsoft 365

O modelo de aplicativo Introdução permite que você traga o poder de Microsoft 365 caminhos de aprendizagem dentro de Microsoft Teams. Este modelo de aplicativo permite que você conceda fácil acesso a páginas de treinamento específicas ou outros ativos intranet e carregue o conteúdo diretamente dentro de Teams. Você também pode alterar o nome do aplicativo ou logotipo para combinar com a marca da sua empresa.

[Colocá-lo em GitHub](https://github.com/msft-teams/tools/tree/master/M365%20Learning%20Pathways)

## <a name="appointment-manager"></a>Gerente de Nomeação 

O Appointment Manager é um modelo de aplicativo Teams para ajudar as empresas a criar, gerenciar e realizar compromissos virtuais com os consumidores através de Teams. Novas solicitações de consulta dos consumidores são visíveis nos canais Teams, onde são rapidamente atribuídos e transferidos para funcionários de uma equipe. As solicitações de nomeação são visualizadas em níveis de equipe ou pessoais através de guias personalizadas. Cada consulta está associada a uma reunião on-line Teams, portanto, a equipe e os consumidores podem facilmente participar da reunião no horário agendado.

O modelo do aplicativo se integra com o Microsoft Bookings para fácil gerenciamento de consultas. Os compromissos agendados aparecem automaticamente nos calendários dos funcionários designados, e os consumidores recebem notificações e lembretes de e-mail personalizáveis com links de reunião incorporados.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-appointment-manager)

![Gerente de consulta geral ](../assets/images/appointment-manager-overview.png)
 ![ em Teams](../assets/images/appointment-manager-2.png)

## <a name="ask-away"></a>Pergunte

Ask Away é um [bot Microsoft Teams](../bots/what-are-bots.md) que permite que os usuários realizem perguntas e respostas, chamadas de sessões Q&A dentro de Teams. Usando o bot Ask Away, os membros da equipe podem enviar e levantar perguntas compartilhadas por colegas que permitem que os hosts Q&A facilmente reúnam perguntas de primeira linha dentro de um canal ou bate-papo. O bot é usado para realizar uma sessão de Q&A em tempo real em uma reunião de Teams e permite que os participantes enviem perguntas ao vivo através do chat.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-askaway)

:::row:::
  :::column span="2":::
    ![Veja o diálogo pop-up da tabela de classificação para os usuários votarem em perguntas](../assets/images/ask-away-app.png)  
:::column-end:::
:::row-end:::

## <a name="associate-insights"></a>Informações associadas

O Associate Insights é um modelo [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que capacita os trabalhadores da primeira linha a capturar e enviar diretamente a opinião, o sentimento e a percepção do cliente. Os trabalhadores da firstline são frequentemente os primeiros representantes da empresa a se envolver com os clientes em um ponto de contato de um para um. Os dados coletados são compartilhados e utilizados de forma colaborativa pelas equipes de negócios, como por meio de uma guia de Power BI Teams, para melhoria do produto e melhoria da experiência do cliente.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-associateinsights)

:::row:::
  :::column span="2":::
    ![Visão de feedback de insights gerados pelo aplicativo](../assets/images/associate-insights-app.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Power BI visão de insights gerados pelo aplicativo](../assets/images/associate-insights-app2.png)
:::column-end:::
:::row-end:::

## <a name="attendance"></a>Participação

O aplicativo De Presença é uma [guia Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que está presa em uma equipe. Ele foi projetado para registrar presença em cenários, como ambientes de aprendizagem e treinamento. Os usuários podem marcar ou editar atendimento por até 30 dias no passado e visualizar relatórios de atendimento resumidos para um grupo inteiro ou participantes individuais. Para obter mais informações sobre o atendimento das equipes, consulte [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance).

A imagem a seguir exibe a demonstração do aplicativo de atendimento:  

![Demonstração do aplicativo de atendimento](../assets/images/attendance-app.png)

## <a name="book-a-room"></a>Livro-a-sala

Book-a-room é um [bot Microsoft Teams](../bots/what-are-bots.md) que permite aos usuários encontrar e reservar rapidamente uma sala de reunião por 30, 60 ou 90 minutos a partir do momento atual. O tempo padrão é de 30 minutos. Os escopos do robô Book-a-room para conversas pessoais ou 1:1. Para obter mais informações sobre o aplicativo Book-a-room, consulte [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom).  
A imagem a seguir exibe a demonstração book-a-room:

![Demonstração de livro-a-room](../assets/images/book-a-room.png)

## <a name="building-access"></a>Acesso ao edifício

Building Access é um aplicativo baseado em [Microsoft Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) que suporta a administração de limites de ocupação predial e normas de distanciamento social, permitindo que os diretores de instalações gerenciem, rastreiem e informem a presença dos funcionários no local. O aplicativo, construído usando [Power Apps](/powerapps/powerapps-overview)e [Power Automate](/power-automate/getting-started)da Microsoft, integra profundamente com Microsoft Teams e permite que as organizações determinem a prontidão para a construção, estabeleçam critérios de elegibilidade para acesso no local e reúnam insights para o planejamento futuro.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-buildingaccess)

:::row:::
   :::column span="":::
     ![Cartão de reserva do Building Access](../assets/images/building-access-reservation.png)
   :::column-end:::
   :::column span="":::
      ![Exibição da chave do Building Access](../assets/images/building-access-access-key.png)
   :::column-end:::
:::row-end:::

## <a name="celebrations"></a>Celebrações

Celebrations é um aplicativo Teams que ajuda os membros da equipe a celebrar os aniversários uns dos outros, aniversários e outros eventos recorrentes. Ele lembra ocasiões especiais de todos os membros da equipe e envia uma mensagem amigável em todas as equipes selecionadas no momento da criação do evento, para fazer com que os membros da equipe se sintam especiais em seu dia.

O aplicativo fornece uma interface fácil para todos os membros da equipe adicionarem e visualizarem seus eventos pessoalmente e também permite que o usuário selecione as equipes em que os eventos são compartilhados.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="checklist"></a>Lista de verificação

Checklist é um aplicativo de [extensão de mensagens](../messaging-extensions/what-are-messaging-extensions.md) Microsoft Teams personalizado que permite que você colabore com sua equipe criando uma lista de verificação compartilhada em um chat ou canal. O aplicativo é suportado em todos os clientes Teams plataforma, como navegador de desktop, iOS e Android. O aplicativo está pronto para implantação como parte de sua assinatura de Microsoft 365.  

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-checklist-app)

:::row:::
:::column span="2":::
    ![Criar checklist na exibição Teams](../assets/images/checklist-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="classroom-drop-in"></a>Drop-in em sala de aula 

O Classroom Drop-in é um aplicativo baseado na [Microsoft Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)que permite que os líderes do sistema encontrem equipes de classe, significa salas de aula virtuais e adicionem a si mesmos ou outros a essas equipes de classe por um período de drop-in especificado, conforme necessário. O aplicativo construído usando [Power Apps](/powerapps/powerapps-overview) e [Power Automate](/power-automate/getting-started)da Microsoft, integra profundamente com Microsoft Teams para garantir que os institutos educacionais possam otimizar suas operações em um ambiente de aprendizagem híbrido, fornecendo acesso a stakeholders relevantes para equipes de classe por requisitos de negócios.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-classroom-dropin)

![Solicitação de drop-in em sala de aula](../assets/images/classroom-drop-in-request.png)

## <a name="company-communicator"></a>Communicator da empresa

O aplicativo Communicator empresa permite que as equipes corporativas criem e enviem mensagens destinadas a várias equipes ou grande número de funcionários por chat, permitindo que a organização chegue aos funcionários exatamente onde eles colaboram. Utilize este modelo para vários cenários, como anúncios de novas iniciativas, onboarding de funcionários, aprendizado moderno e desenvolvimento ou transmissões em toda a organização.

O aplicativo fornece uma interface fácil para usuários designados criarem, visualizarem, colaborarem e enviarem mensagens.

Ele fornece uma base para construir recursos de comunicação direcionados personalizados, como telemetria personalizada, quantos usuários reconheceram ou interagiram com uma mensagem.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![jCompany Communicator compor vista de caixa](../assets/images/CompanyCommunicatorCompose.png)

## <a name="contact-group-lookup"></a>Procurar grupo de contato

O aplicativo Contact Group Lookup fornece uma abordagem conveniente e útil para criar, acessar e gerenciar os grupos de contato da sua organização, anteriormente conhecidos como listas de distribuição ou grupos de comunicação. Os usuários podem visualizar e conversar rapidamente com os membros do grupo, visualizar o status do membro e criar um bate-papo em grupo com membros selecionados no grupo de contato, tudo dentro do ambiente Teams.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-app-contactgrouplookup)

:::row:::
:::column span="2":::
    ![Grupo de contato Procura-se fixada visualização de favoritos](../assets/images/contact-group-lookup-favorites.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Demonstração de bate-papo de início de grupo de contato](../assets/images/contact-group-lookup-chat.png)
:::column-end:::
:::row-end:::

## <a name="co-worker-appreciation"></a>Valorização do colega de trabalho 

Usando o modelo de valorização do colega de trabalho em Microsoft Teams, os usuários podem reconhecer as conquistas de seus colegas no contexto Teams. Quando os colegas de trabalho escolhem recompensar um colega, os destinatários e outros membros da equipe são marcados em uma conversa de canal e recebem uma notificação sobre os detalhes do prêmio do canal. Os prêmios são registrados no aplicativo Teams, que é seguro, portátil e facilmente compartilhável. Esta é considerada como a versão baseada no PowerApps do modelo de aplicativo Open Badges, com uma tabela de classificação.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-coworker-appreciation)

![geral](../assets/images/coworker-appreciation-1.png)

## <a name="crowdsourcer"></a>CrowdSourcer

CrowdSourcer é um [bot Microsoft Teams](../bots/what-are-bots.md) que fornece às equipes informações consultadas de forma colaborativa dos membros do grupo. Ele ajuda a responder perguntas frequentes, permitindo que os participantes se envolvam ativamente e contribuam para um recurso de informação divertido e útil.

[Obtê-lo no Github](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Interação do usuário final crowdsource](../assets/images/crowdsourcer.png)

## <a name="custom-stickers"></a>Adesivos personalizados

A auto-expressão é o cerne de uma cultura de equipe saudável. Este modelo de aplicativo é uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) que permite que seus usuários usem adesivos e GIFs personalizados dentro de Microsoft Teams. Este modelo oferece uma experiência de configuração fácil baseada na Web, onde qualquer pessoa com acesso à configuração pode carregar os GIFs, adesivos e imagens que deseja que seus usuários tenham, permitindo que toda a sua equipe use qualquer conjunto de adesivos que você escolher.

Este aplicativo também permite o fácil compartilhamento de imagens, GIFs, adesivos entre as equipes sem precisar de acesso a sites SharePoint ou canais individuais como mecanismos de armazenamento e compartilhamento. Por exemplo, as equipes de produtos podem facilmente compartilhar imagens de produtos e GIFs para mídias sociais, marketing e equipes de vendas programáticamente. Também pode-se estender este aplicativo acionando um fluxo de notificação para equipes ou indivíduos específicos quando novas imagens e GIFs são disponibilizados.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![Aplicativo de adesivos](../assets/images/stickers.png)

## <a name="employee-ideas"></a>Ideias dos funcionários

O aplicativo Ideias de Funcionários é a versão PowerApps do modelo de aplicativo Great Ideas baseado no Azure. O aplicativo permite que os usuários Teams configurem e configurem uma campanha de ideias. Uma campanha de ideias é uma categoria para agrupar ideias em torno de temas comuns.

Teams usuários também podem realizar as seguintes atividades:

* Configure um formulário de submissão padrão que os funcionários devem enviar para cada ideia. 
* Revise e gerencie as ideias e lista de campanhas.
* Modifique e exclua campanhas.
* Revise os quadros de líderes de ideias.
* Vote e compartilhe ideias prioriadas.
* Envie ideias para uma campanha.
* Veja a ideia de outro membro da equipe.
* Vote nas ideias mais curtidas.
* Reveja o desempenho de suas ideias em comparação com outras dentro de uma campanha.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-employeeideas)

![Gerenciar a exibição da campanha](../assets/images/employee-ideas-manage-campaigns.png) 

## <a name="e-prescriptions"></a>Prescrições eletrônicos 

O E-Prescriptions é um aplicativo baseado em [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que melhora a telemedicina e o cuidado virtual, automatizando o processo de emissão de prescrições e-prescritas aos pacientes. Os profissionais médicos podem revisar rapidamente as consultas, gerar prescrições e e-mails com anexos de prescrição e para pacientes diretamente dentro da plataforma Teams.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-eprescription) 

:::row:::
:::column span="2":::
    ![Captura de tela do aplicativo E-Prescrições. Mostra como um profissional de saúde pode selecionar um botão de geração para pedir uma prescrição para um paciente.](../assets/images/e-prescriptions-app-template.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Captura de tela do aplicativo E-Prescrições. Mostra como os administradores podem gerenciar os prestadores de cuidados de saúde que usam o aplicativo.](../assets/images/e-prescriptions-app-template-admin.png)
:::column-end:::
:::row-end:::

## <a name="employee-training"></a>Treinamento de Funcionários 

O treinamento de funcionários é um aplicativo Microsoft Teams que permite aos organizadores publicar, rastrear e promover eventos de aprendizagem e treinamento para sua organização.  Com o aplicativo, os planejadores de eventos podem enviar lembretes e notificações para os inscritos do evento e os funcionários podem indicar interesse em eventos futuros, manter-se atualizado sobre eventos atuais e compartilhar detalhes do evento com os colegas através da extensão de mensagens Teams.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-employeetraining)

:::row:::
:::column span="2":::
    **Veja eventos de treinamento de funcionários** ![ Imagem da guia de treinamento dos funcionários](../assets/images/employee-training-discover-tab.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    **Crie um evento de treinamento de funcionários** ![ Treinamento de funcionários cria formulário de evento](../assets/images/employee-training-create-event.jpg)
:::column-end:::
:::row-end:::

## <a name="expert-finder"></a>Expert Finder

Expert Finder é um [bot Microsoft Teams](../bots/what-are-bots.md) que identifica membros específicos da organização com base em suas habilidades, interesses e atributos de educação. Os membros encontram especialistas dentro de uma organização que correspondem a uma pesquisa de palavras-chave de Azure Active Directory perfis de usuários.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demonstração de resultados de pesquisa do Expert Finder](../assets/images/expert-finder.png)

## <a name="faq-plus"></a>Perguntas Frequentes Plus

Q conversacional&A bots são uma maneira fácil de fornecer respostas para perguntas frequentemente feitas pelos usuários. Mas, a maioria dos bots não consegue se envolver com os usuários de forma significativa porque não há nenhum humano no loop quando o bot falha. Faq bot é um Q amigável&um bot que traz um humano no loop quando ele é incapaz de ajudar. Pode-se fazer uma pergunta ao bot e o bot responde com uma resposta se ele estiver contido na base de conhecimento. Caso não, o bot permite que o usuário envie uma consulta que, em seguida, é postada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte agindo sobre as notificações de dentro da própria equipe.

> [!NOTE]
> A versão mais recente do **FAQ Plus** suporta resoluções de Q&A aprimoradas, permitindo que uma equipe de especialistas complete o seguinte:
>
> &#x2714; Adicione novas&Q diretamente à base de conhecimento usando extensões de mensagens.
>
> &#x2714; Editar e excluir q&A pares adicionados por um bot.
>
> &#x2714; Acompanhe a história de revisão do Q&As.
>
> &#x2714; Configure uma resposta com detalhes adicionais para exibir como uma [placa adaptativa](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).
>
[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)

![FAQ Plus gif](../assets/images/FAQPlusEndUser.gif)

## <a name="get-support-app"></a>Obter aplicativo de suporte

O aplicativo Get Support é usado por organizações que estão usando Microsoft Teams, para permitir que qualquer conjunto de usuários solicite assistência aos supervisores. Este aplicativo inclui os seguintes recursos:
* Solicitando assistência em diferentes categorias de um Aplicativo de Energia.
* Notificações enviadas aos solicitantes informando-os de quem lebre atribuiu.
* Notificações enviadas aos supervisores designados informando-os de quem precisa de assistência. 
* Analisando escaladas e padrões em SharePoint e PowerBI.S.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-app-get-support/)

![Obter gif de suporte](../assets/images/get-support.gif)

## <a name="goal-tracker"></a>Rastreador de metas

O aplicativo Goal Tracker é uma solução abrangente para sua organização apoiar o estabelecimento de metas, observando o progresso e reconhecendo o sucesso dentro de Microsoft Teams. O aplicativo permite que os usuários desvelem, rastreiem e atualizem objetivos em nível profissional, pessoal e de equipe. Os membros da equipe também recebem lembretes oportunos e atualizações de status para permanecer focados e manter-se no caminho certo.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-app-goaltracker)

:::row:::
  :::column span="2":::
    ![Definir metas](../assets/images/goal-tracker-set-goals-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ver metas definidas](../assets/images/goal-tracker-your-goals-view.png)
:::column-end:::
:::row-end:::

## <a name="great-ideas"></a>Grandes Ideias

O aplicativo Great Ideas apoia e capacita a inovação e a criatividade dentro de sua organização. O aplicativo permite que seus funcionários compartilhem ideias com colegas e liderança, descubram novas submissões, contribuições de destaque para consideração por pares e votem nas melhores propostas dentro de Microsoft Teams.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-greatideas)

:::row:::
  :::column span="2":::
    ![Exibir ideias submetidas](../assets/images/great-ideas-all-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ver ideias](../assets/images/great-ideas-digest-view.png)
:::column-end:::
:::row-end:::

## <a name="group-activities"></a>Atividades em grupo

O Group Activities é um aplicativo Microsoft Teams que facilita que os proprietários de equipes criem rapidamente grupos de atividades e gerenciem fluxos de trabalho de colaboração no contexto de Microsoft Teams. Os autores de atividades são habilitados a criar atividades, distribuir aleatoriamente membros da equipe em grupos e, opcionalmente, fazer com que o bot envie lembretes até que as atividades sejam concluídas.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-groupactivities)

:::row:::
  :::column span="2":::
    ![Lista de atividades em grupo em Teams](../assets/images/group-activities-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Mensagem de notificação de atividades em grupo em um canal](../assets/images/group-activities-2.png)
:::column-end:::
:::row-end:::

## <a name="group-connect-9734"></a>Conexão &#9734; do Grupo

O Group Conexão é um aplicativo Microsoft Teams que ajuda os membros da organização a descobrir grupos de funcionários e a encontrar informações relevantes para grupos de funcionários. O aplicativo vem embutido com ricas capacidades para os líderes da organização se comunicarem com seus funcionários sobre grupos, eventos e recursos. O aplicativo Group Conexão também combina os membros do grupo entre si na frequência desejada para incentivar a rede e a coesão dentro de um grupo. Para obter mais informações sobre como você pode aproveitar o aplicativo Group Conexão para ajudar os grupos de funcionários a promover dentro de sua organização, consulte o aplicativo em GitHub.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-groupconnect)

![Descubra grupos D&I](https://github.com/OfficeDev/microsoft-teams-apps-diversityandinclusion/wiki/Images/temp_group_connect_landing.png)

## <a name="grow-your-skills"></a>Cresça suas habilidades

O aplicativo Grow Your Skills apoia o crescimento e o desenvolvimento profissional, permitindo que os funcionários contribuam para projetos suplementares para sua organização e, ao mesmo tempo, aprendam novas habilidades. Os funcionários podem usar o aplicativo para localizar oportunidades que atendam aos seus interesses, desfrutem de colaboração significativa com os pares e adquiram novos níveis de experiência e recursos, tudo dentro do ambiente Teams.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-growyourskills)

:::row:::
  :::column span="2":::
    ![Visualização de projetos disponíveis](../assets/images/grow-your-skills-all-projects-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Visão de habilidades adquiridas pelo espectador](../assets/images/grow-your-skills-acquired-skills-view.png)
:::column-end:::
:::row-end:::

## <a name="hr-support"></a>Suporte de RH

O bot de suporte de RH é um robô Q amigável&um bot que traz um profissional de suporte ou especialista da equipe de RH no loop quando ele não pode ajudar. Pode-se fazer uma pergunta ao bot e o bot responde com uma resposta se ele estiver contido na base de conhecimento. Caso não, o bot permite que o usuário envie uma consulta que, em seguida, é postada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte agindo sobre as notificações de dentro de sua própria equipe. Além disso, o bot sugere links para políticas de RH recomendadas ou perguntas, procurando por tags pré-configuradas na questão. Estas telhas são encontradas na guia associada como uma referência rápida. O Suporte de RH funciona bem para o peso leve Q&A e para fornecer suporte rápido ao lançar novos projetos ou iniciativas na organização.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![Suporte de RH](../assets/images/expert-user.png)

## <a name="icebreaker"></a>Frases de apresentação

Icebreaker é um [bot Microsoft Teams](../bots/what-are-bots.md) que ajuda sua equipe a se aproximar, emparelhando dois membros aleatórios da equipe a cada semana para se encontrar. O bot facilita o agendamento, sugerindo automaticamente horários livres que funcionam para ambos os membros. Fortaleça conexões pessoais e construa uma comunidade de malha com este aplicativo.

Além de incentivar conexões pessoais em toda a sua equipe, o aplicativo Icebreaker pode ajudar a cultivar comunidades baseadas em interesse dentro de sua organização. Por exemplo, você pode usar este aplicativo para um grupo de interesse DevOps para ajudar ideias e práticas recomendadas organicamente espalhadas por toda a sua organização.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Aplicativo icebreaker](../assets/images/icebreaker.png)

## <a name="incentives"></a>Incentivos

Os incentivos são um modelo [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que gerencia e acompanha a participação incentivada dos colaboradores em atividades designadas, como treinamentos e iniciativas de gestão de mudanças. Os administradores usam o aplicativo para estabelecer atividades designadas, atribuir pontos para conclusão e especificar níveis de ponto de elegibilidade necessários para recompensas. Os funcionários usam o aplicativo para visualizar seus pontos acumulados e, ao atingir a elegibilidade, solicitar e reivindicar recompensas resgatáveis.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-incentives)

![Demonstração do aplicativo de incentivos](../assets/images/incentives-app.png)

## <a name="incident-reporter"></a>Repórter de Incidente

Incident Reporter é um [bot Microsoft Teams](../bots/what-are-bots.md) que otimiza a gestão de incidentes em sua organização. O bot facilita a coleta automatizada de dados de incidentes, relatórios personalizados de incidentes, notificações relevantes das partes interessadas e rastreamento de incidentes de ponta a ponta.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-incidentreport)

:::row:::
  :::column span="2":::
    ![Visão de escopo do grupo de repórteres incidentes](../assets/images/incident-reporter-02.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Visão de escopo pessoal do repórter incidente](../assets/images/incident-reporter-01.jpg)
:::column-end:::
:::row-end:::

## <a name="inspection"></a>inspeção 

 A inspeção é um aplicativo Microsoft Teams que permite que os trabalhadores da linha de frente inspecionem qualquer coisa, desde locais até ativos e equipamentos. Por exemplo, uma loja de varejo, fábrica ou veículos e máquinas. Existem dois aplicativos nesta solução, cada um destinado a diferentes tipos de usuários.

O aplicativo capacita os trabalhadores da linha de frente a inspecionar um ativo ou área, gerenciar a qualidade dos produtos e serviços ou manter a segurança no local de trabalho. Facilita a comunicação entre os membros da equipe para resolver problemas encontrados durante a inspeção. O aplicativo fornece relatórios simples para os gestores agilizarem a resolução de problemas e destacarem tendências.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-inspection)

 ![Visão geral da inspeção](../assets/images/inspection-app.png)  


## <a name="issue-reporting"></a>Relatórios de problemas

O aplicativo Issue Reporting capacita os funcionários e gestores a levantar e gerenciar problemas. Ele consiste em dois aplicativos, aplicativo de relatórios de em questão para problemas de emissão e aplicativo Gerenciar problemas para gerenciar problemas.

Os gerentes de equipe usam o aplicativo Gerenciar problemas para configurar a experiência do aplicativo, incluindo o canal no qual Microsoft Teams mensagens e tarefas do Planner são criadas pelo aplicativo. Os gerentes também usam o aplicativo para criar formulários de modelo para coletar detalhes quando um usuário relata um problema. Por exemplo, revisar, editar ou excluir formulários de modelo de problema. O aplicativo também é usado para revisar problemas da equipe, relatar o histórico de problemas e gerenciar eficientemente a resolução de problemas.

Os funcionários usam o aplicativo de relatórios de problemas para registrar problemas e detalhes necessários para resolvê-los. O aplicativo também é usado para modificar e resolver problemas existentes e obter uma visão de alto nível dos problemas individuais ou de equipe.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-issuereporting)

![Exibição da equipe de relatórios de problemas](../assets/images/issue-reporting-team-view.png)  

## <a name="new-employee-onboarding"></a>Novo onboarding de funcionários 

O New Employee Onboarding é uma solução integrada de Microsoft Teams e [SharePoint Novo Onboarding de Funcionários](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) que permite que sua organização forneça uma experiência de onboarding consistente e de alta qualidade para os funcionários em sua jornada de contratação nova. O aplicativo é usado por equipes de recursos humanos e gerentes de contratação para fornecer informações relevantes durante todo o processo de orientação e indução e por novas contratações para compartilhar feedback, fornecer introduções e tarefas completas de onboarding.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding)

:::row:::
  :::column span="2":::
    **Novo cartão de boas-vindas do funcionário** ![ Imagem do novo cartão de boas-vindas do funcionário](../assets/images/new-employee-welcome-card.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    **Nova lista de verificação de funcionários** ![ Imagem da nova lista de verificação de funcionários](../assets/images/new-employee-checklist.png)  
:::column-end:::
:::row-end:::

## <a name="open-badges"></a>Crachás Abertos

Open Badges é um aplicativo Microsoft Teams que permite que os indivíduos ganhem crachás de credenciais de aprendizagem digital dentro do contexto Teams e compartilhem-nos em todos os lugares. Usando recursos da autoridade de emissão de crachás digitais de terceiros, [o Badgr](https://badgr.org/), crachás premiados são registrados no perfil Badgr de um destinatário e disponíveis para construir e compartilhar uma rica imagem das jornadas de aprendizagem ao longo da vida.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-openbadges)

:::row:::
  :::column span="2":::
    ![Imagem dos crachás disponíveis](../assets/images/open-badges-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de crachás premiados](../assets/images/open-badges-2.png)
:::column-end:::
:::row-end:::

## <a name="poll"></a>pesquisa 

A enquete é um aplicativo personalizado de [extensão de mensagens](../messaging-extensions/what-are-messaging-extensions.md) Microsoft Teams que permite criar e enviar pesquisas rapidamente em um chat ou um canal para reunir opiniões e preferências da equipe. O aplicativo é suportado em todos os clientes Teams plataforma, como desktop, navegador, iOS e Android e está pronto para implantação como parte de sua assinatura Microsoft 365.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-poll-app)

:::row:::
  :::column span="1":::
    ![Criar enquete em Teams visualização](../assets/images/poll-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="quick-responses"></a>Respostas rápidas

Quick Responses é um aplicativo Microsoft Teams que oferece uma solução robusta para responder efetivamente às perguntas dos usuários perguntas frequentes. Em vez de responder a cada consulta manual e continuamente repetindo informações, o aplicativo constrói uma biblioteca de respostas para uma experiência interativa do usuário através de [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md)Teams .

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-quickresponses)

![Visão amostral das respostas](../assets/images/quick-responses.png)

## <a name="quiz--9734"></a>&#9734; de quiz

Quiz é um aplicativo de [extensão de mensagens Teams](../messaging-extensions/what-are-messaging-extensions.md) personalizado que permite criar um quiz dentro de um chat ou um canal para verificação de conhecimento e resultados instantâneos. Você pode usar quiz para, exames in-class e off-line, verificação de conhecimento dentro da equipe, e para testes divertidos dentro de uma equipe. O aplicativo Quiz é suportado em várias plataformas, como Teams clientes desktop, navegador, iOS e Android. Este aplicativo está pronto para implantação como parte de sua assinatura Microsoft 365 existente.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-quiz)

:::row:::
  :::column span="1":::
    ![Criar quiz na exibição Teams](../assets/images/quiz-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="rapid-assist"></a>Assistência rápida

Rapid Assist é um aplicativo baseado em [Microsoft Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) que permite que os associados que enfrentam os clientes se conectem rapidamente com os especialistas para obter respostas rápidas, procurar informações, acompanhar solicitações abertas e permitir que especialistas recebam notificações para receber rapidamente uma chamada para ajudar a responder perguntas. O aplicativo construído usando [Power Apps](/powerapps/powerapps-overview) e [Power Automate](/power-automate/getting-started)da Microsoft, integra-se profundamente com Microsoft Teams para permitir que as organizações conectem facilmente os trabalhadores da linha de frente com as ligações corporativas para resolver consultas ao cliente e oferecer uma ótima experiência ao cliente. 

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-rapid-assist)

:::row:::
   :::column span="":::
     ![Interface de solicitação de usuário final](../assets/images/EndUserHome.png)
   :::column-end:::
   :::column span="":::
      ![Visão de solicitação de especialista](../assets/images/ExpertViewRequests.png)
   :::column-end:::
:::row-end:::

## <a name="reflect"></a>refletir 

Reflect é um aplicativo personalizado de [extensão de mensagens](../messaging-extensions/what-are-messaging-extensions.md) Microsoft Teams que fornece um recurso seguro e inclusivo para que seus membros da equipe compartilhem o estado de seu bem-estar emocional com colegas ou líderes de grupo diretamente dentro de Teams. O aplicativo está disponível em chats de canal, grupo, reunião e 1:1 e a resposta de check-in é definida para público, privado para remetente ou totalmente anônimo.

[Colocá-lo em GitHub](https://github.com/OfficeDev/Microsoft-Teams-App-Reflect)

:::row:::
    :::column:::
    **Pesquisa de bem-estar**
    
    ![Refletir enquete de usuários de aplicativos](../assets/images/reflect-app-user-poll.png)
    :::column-end:::
:::row-end:::

## <a name="remote-support"></a>Suporte remoto

O Remote Support é um [bot Microsoft Teams](../bots/what-are-bots.md) que fornece uma interface focada entre solicitantes de suporte em toda a sua organização e a equipe de suporte interno.  Os usuários finais podem enviar, editar ou retirar solicitações de suporte e a equipe de suporte pode responder, gerenciar e atualizar solicitações todas dentro da plataforma Teams.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-remotesupport)

:::row:::
  :::column span="2":::
    ![Formulário de suporte de solicitação](../assets/images/remote-support-request-form.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Solicitar detalhes de suporte](../assets/images/remote-support-request-details.jpg)
:::column-end:::
:::row-end:::

## <a name="request-a-team"></a>Solicitação-a-equipe

Request-a-team é um aplicativo Microsoft Teams que otimiza a criação de novas equipes para sua organização corporativa. O aplicativo suporta padronização e práticas recomendadas ao criar novas instâncias de equipe através da integração de um formulário de solicitação guiado por assistente, um processo de aprovação incorporado, um painel de status de solicitação e compilações automatizadas da equipe.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-requestateam)

:::row:::
  :::column span="2":::
    ![Exibição da página de início de uma equipe](../assets/images/request-a-team-two.jpg)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Visualização da página do assistente de solicitação por equipe](../assets/images/request-a-team-three.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-channels"></a>Scrums para Canais

Scrums for Channels é um aplicativo de assistente scrum que permite que os usuários agendem e executem scrums em canais dentro de Microsoft Teams. O aplicativo é ótimo para equipes remotas e equipes compostas por membros de locais geográficos variados e fusos horários para compartilhar atualizações diárias e garantir a participação em reuniões de stand-up scrum.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforchannels)

> [!NOTE]
> Para realizar reuniões de scrum em um bate-papo em grupo, consulte o modelo de aplicativo [Scrums for Group Chat.](#scrums-for-group-chat)

:::row:::
  :::column span="2":::
    ![Scrums para visualização de configurações de canais](../assets/images/scrum-for-channels-settings.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Scrums para canais de visualização de status de membro da equipe](../assets/images/scrum-for-channels-status.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-group-chat"></a>Scrums para bate-papo em grupo

> [!NOTE]
> O modelo do aplicativo Scrums Status é atualizado e agora é Scrums for Group Chat.

Scrums for Group Chat é um assistente de suporte que permite que os membros do chat em grupo executem reuniões de stand-up assíncronsas e compartilhem facilmente suas atualizações diárias. Ele permite que todos os membros do chat de grupo contribuam para o scrum e visualizem as atualizações feitas por outros no scrum em execução.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforgroupchat)

![Scrums para demonstração de bate-papo em grupo](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="share-now"></a>Compartilhar agora 

O aplicativo Share Now promove a troca positiva de informações entre colegas, permitindo que seus usuários compartilhem facilmente conteúdo dentro do ambiente Teams. Os usuários engajam o aplicativo para compartilhar itens de interesse com os membros da equipe, descobrir novos conteúdos compartilhados, definir preferências e marcar favoritos para leitura posterior.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-sharenow)

![Selecione a exibição de conteúdo](../assets/images/share-now-suggested-content.png)

## <a name="sharepoint-list-search"></a>Pesquisa de lista do SharePoint

A colaboração em Microsoft Teams frequentemente faz referência às informações contidas nos itens em uma lista SharePoint. Colar um link para o item em questão força todos a mudar o contexto da conversa, encontrar as informações necessárias e, em seguida, retornar ao Teams para continuar a conversa. À medida que a conversa continua, as pessoas têm que voltar ao item de referência várias vezes para verificar novos comentários e atualizar suas memórias das informações contidas no item. Essa comutação de contexto cria uma barreira para uma colaboração suave.
Para resolver esse problema, o modelo do aplicativo Listar busca é usado. Muitos usuários usam SharePoint para alimentar alguns dos principais fluxos de trabalho em suas organizações. No entanto, colaborar em torno de listas é difícil. Usando o modelo do aplicativo List Search em Microsoft Teams, os usuários podem inserir informações de SharePoint listar itens diretamente dentro de uma conversa de chat para aliviar a troca de contexto causada ao simplesmente inserir um link em um chat. As informações são inseridas como um cartão auto-formatado fácil de ler, ajudando os usuários a permanecerem engajados na conversa.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Aplicativo de pesquisa de listas](../assets/images/list-search-template.png)

## <a name="staff-check-ins"></a>Check-ins da equipe

O Staff Check-ins é um aplicativo baseado em [Power Apps](/powerapps/powerapps-overview) que permite a comunicação de supervisão entre sua empresa e pessoal de campo. A equipe pode facilmente fornecer informações críticas e atualizações de status em uma base agendada ou ad-hoc diretamente de Teams. O aplicativo suporta localização em tempo real, fotos, notas, notificações de lembrete e fluxos de trabalho automatizados.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-staffcheckins)

![Criar exibição de check-in](../assets/images/staff-check-ins-create.png)

## <a name="survey"></a>Pesquisa

O Survey é um aplicativo personalizado de [extensão de mensagens](../messaging-extensions/what-are-messaging-extensions.md) Microsoft Teams que permite criar uma pesquisa em um chat ou um canal para coletar dados e obter insights acionáveis. O aplicativo é suportado em todos os clientes Teams plataforma, como desktop, navegador, iOS e Android e está pronto para implantação como parte de sua assinatura Microsoft 365.  

[Colocá-lo em GitHub](https://github.com/OfficeDev/Microsoft-Teams-Survey-app)

:::row:::
  :::column span="2":::
    ![Criar pesquisa em Teams visualização](../assets/images/survey-app-template-compose-view.gif)
:::column-end:::
:::row-end:::

## <a name="time-tally"></a>Contagem de tempo 

Um projeto pode incluir várias tarefas, e vários projetos podem ser atribuídos aos funcionários. Os gestores são obrigados a entender o andamento do projeto através do tempo gasto pelos colaboradores nessas tarefas. Isso pode ser uma atividade complicada, pois os funcionários precisam preencher as planilhas de tempo. O aplicativo Time Tally permite que os funcionários preencham suas planilhas de tempo rapidamente, usando o dispositivo móvel, e os gerentes não têm que acompanhar os funcionários na entrada da folha de tempo. Os gestores podem visualizar a utilização do projeto com base em recursos, e podem aprovar ou rejeitar as entradas. As notificações de lembrete são enviadas para garantir a conformidade com a folha de tempo. Além disso, dados históricos e utilizaçãos estão disponíveis para análise.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-timetally)

![Contagem de tempo](../assets/images/11zon_gif.gif)

## <a name="training--9734"></a>&#9734; de treinamento

O Training é um aplicativo personalizado [de extensão de mensagens Teams](../messaging-extensions/what-are-messaging-extensions.md) que permite que os usuários publiquem um treinamento dentro de um chat ou um canal para compartilhamento de conhecimento offline e upskilling. O aplicativo é suportado em vários clientes Teams plataforma, como desktop, navegador, iOS e Android. Este aplicativo está pronto para implantação como parte de sua assinatura de Microsoft 365.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-training)

:::row:::
  :::column span="1":::
    ![Criar treinamento na visão Teams](../assets/images/training-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="virtual-rounding"></a>Arredondamento Virtual

Os prestadores de serviços hospitalares e de emergência fazem muitas **rondas** por dia. Esses check-ins rápidos nos pacientes destinam-se a fornecer uma verificação de status sobre como o paciente está indo e garantir que as preocupações do paciente sejam tratadas. Embora o arredondamento seja uma prática essencial para garantir que os pacientes estejam sendo monitorados por vários tipos de provedores, eles representam um enorme dreno no EPI, pois para cada visita, de cada provedor, uma nova máscara e um novo conjunto de luvas são usados. Com estes modelos de aplicativos, os profissionais médicos podem facilmente realizar rodadas virtualmente, através de uma Microsoft Teams reunião entre o provedor e o paciente.

A solução virtual de arredondamento também é referenciada no post do [blog](https://aka.ms/teamsvirtualrounding)Microsoft Health and Life Sciences .

[Colocá-lo em GitHub](https://github.com/SmartterHealth/Virtual-Rounding)

![Arredondamento Virtual](../assets/images/virtual-rounding-overview.png)

## <a name="visitor-management"></a>Gestão de Visitantes

O aplicativo de Gerenciamento de Visitantes permite que sua organização e funcionários gerenciem de forma fácil e eficiente o processo de visitantes no local, diretamente a partir de Microsoft Teams. O aplicativo permite que os funcionários criem solicitações de visitantes, rastreiem centralmente um status de solicitação através do painel de visitantes e recebam notificações em tempo real quando um visitante chega.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-app-visitormanagement)

:::row:::
  :::column span="2":::
    ![Crie uma exibição de solicitação](../assets/images/visitor-management-create-request.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Notificação de chegada de visitantes](../assets/images/visitor-management-notify-host.png)
:::column-end:::
:::row-end:::

## <a name="workplace-awards"></a>Prêmios do Local de Trabalho

O Workplace Awards é um modelo de aplicativo Teams que fornece uma estrutura positiva para promover o reconhecimento e incentivar a cultura de valorização dos funcionários no ambiente de trabalho moderno. O aplicativo permite que você configure e gerencie recompensas e reconhecimento de funcionários, chamado programa R&R, onde os funcionários podem facilmente nomear e endossar colegas e seu líder R&R pode ver nomeações submetidas, conceder prêmios e anunciar os destinatários.

[Colocá-lo em GitHub](https://github.com/OfficeDev/microsoft-teams-apps-workplaceawards)

:::row:::
  :::column span="2":::
    ![Cartão de indicação de prêmios no local de trabalho ](../assets/images/workplace-awards-nominate.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Guia de lista de prêmios no local de trabalho](../assets/images/workplace-awards-champion-tab.png)
:::column-end:::
:::row-end:::

Para obter mais informações sobre o modelo do aplicativo, consulte [o modelo do Aplicativo](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).

## <a name="see-also"></a>Confira também

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
