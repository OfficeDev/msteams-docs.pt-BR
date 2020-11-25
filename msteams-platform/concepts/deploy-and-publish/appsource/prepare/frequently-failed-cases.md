---
title: Dicas e casos com falhas freqüentes
description: Descreve as dicas para o envio e a maioria das políticas com falha
author: laujan
ms.author: lajanuar
ms.topic: how to
keywords: Validação de aplicativos do Microsoft Teams falha na maioria dos casos de teste com aprovação rápida appsource Publish
ms.openlocfilehash: b1333448eb8b8e1e2310114bf95404b74aa95b58
ms.sourcegitcommit: aca9990e1f84b07b9e77c08bfeca4440eb4e64f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "49409103"
---
# <a name="tips-for-a-successful-app-submission"></a>Dicas para um envio de aplicativo bem-sucedido

Este artigo aborda razões comuns de falha na validação dos aplicativos enviados. Embora não tenha sido projetada para ser uma lista abrangente de todos os problemas em potencial com seu aplicativo, este guia aumentará a probabilidade de que seu envio de aplicativo seja transmitido pela primeira vez. *Consulte* [políticas de certificação do Marketplace comercial](/legal/marketplace/certification-policies) para obter uma lista extensa de políticas de validação.

>[!NOTE]
>A **[seção 1140](/legal/marketplace/certification-policies#1140-teams)** é específica para o Microsoft Teams e a **[subseção 1140,4](https://docs.microsoft.com/legal/marketplace/certification-policies#11404-functionality)** trata dos requisitos de funcionalidade para aplicativos do teams.

## <a name="validation-guidelines--most-failed-test-cases"></a>Diretrizes de validação & os casos de teste mais falharam

### <a name="9989-general-considerations"></a>&#9989; considerações gerais

*Consulte também* a [seção 100 — General](/legal/marketplace/certification-policies#100-general)

* Verifique se você está usando a versão 1.4.1 ou posterior do [SDK do Microsoft Teams](https://www.npmjs.com/package/@microsoft/teams-js).
* Não faça alterações em seu aplicativo enquanto o processo de validação estiver em andamento. Isso exigirá uma revalidação completa do seu aplicativo.
* Seu aplicativo não deve parar de responder, terminar inesperadamente ou conter erros de programação. Se for encontrado um problema, seu aplicativo deverá falhar normalmente e fornecer uma mensagem de encaminhamento à frente para o usuário.
* Seu aplicativo não deve baixar, instalar ou iniciar automaticamente qualquer código executável no ambiente do usuário. Todos os downloads devem buscar permissões explícitas do usuário.
* Qualquer material que você associar à sua experiência, como descrições e documentação de suporte, deve ser preciso. Use a verificação ortográfica, a capitalização, a pontuação e a gramática corretas em suas descrições e materiais.
* Fornecer informações de ajuda e suporte. É altamente recomendável que seu aplicativo inclua um link de ajuda/perguntas frequentes para a experiência do usuário de primeira execução. Para todos os aplicativos pessoais, recomendamos fornecer a página de ajuda como uma guia pessoal para uma melhor experiência do usuário.
* Os aplicativos não devem tirar o usuário do teams para cenários de usuário principais. O uso de guias/módulos de tarefas é recomendado para exibir informações para os usuários do teams.
* Aumente o número de versão do aplicativo no manifesto se você fizer alterações de manifesto no seu envio.
* O aplicativo não deve retirar os usuários do teams para cenários de usuário principais. Os destinos de link em aplicativos não devem ser vinculados a um navegador externo, mas devem ser vinculados a elementos div contidos no Teams, por exemplo, dentro de módulos e guias de tarefas.
* Os aplicativos pessoais permitem que os usuários compartilhem conteúdo de uma experiência de aplicativo pessoal com outros membros da equipe.

### <a name="9989--provide-a-clear-and-simple-sign-insign-out-and-sign-up-experience"></a>&#9989; fornecer uma experiência clara e simples de entrada/saída e inscrição

Seção *Consulte também* [1100,5 — controle de cliente](/legal/marketplace/certification-policies#11005-customer-control)

* Se seu aplicativo ou suplemento depender de contas ou serviços externos, a experiência de entrada/saída e inscrição deverá ser aparente e alcançável em todos os recursos do seu aplicativo.
* Se houver uma opção de entrada explícita fornecida para o usuário, deverá haver uma opção de saída correspondente (mesmo que o aplicativo esteja usando a [autenticação silenciosa](../../../../tabs/how-to/authentication/auth-silent-aad.md)).
* A opção de saída deve apenas desconectar o usuário da capacidade do seu aplicativo e não do cliente do teams.
* No mínimo, a opção de saída deve desconectar o usuário dos mesmos recursos acessados com a opção de entrada. Por exemplo, se a opção de entrada incluir uma extensão de mensagens e uma guia, a opção de saída deve incluir a extensão de mensagens e a guia.

* Certifique-se de que haja sempre uma maneira de reverter os seguintes comportamentos (ou semelhantes):
  * Entrar => sair.
  * Vincular uma conta/serviço => desvincular uma conta/serviço.
  * Conectar uma conta/serviço => desconectar uma conta/serviço.
  * Autorizar uma conta/serviço => desautorizar/negar uma conta/serviço.
  * Registrar uma conta/serviço => cancelar o registro/cancelar a assinatura de uma conta/serviço.
* Se seu aplicativo requer uma conta ou serviço, você deve fornecer uma maneira de o usuário se inscrever ou criar uma solicitação de inscrição. Uma exceção pode ser concedida se seu aplicativo requer uma licença para usar. No entanto, esses cenários confiram uma maneira clara de ser fornecida uma nova assinatura de usuário.
* Certifique-se de fornecer orientação de avanço para um novo usuário sobre como se inscrever para usar seus serviços de aplicativos. Se um link de inscrição pronto não estiver disponível, o modo claro para frente poderá ser fornecido nas seguintes áreas

> [!div class="checklist"]
>
> * nas seções de descrição do seu aplicativo;
> * na mensagem de boas-vindas do aplicativo;
> * na mensagem de ajuda do seu aplicativo;
> * na janela em que você pede que um usuário entre em seus serviços;

* Os aplicativos que não têm um fluxo de inscrição fácil também podem incluir uma guia de ajuda ou um link para uma página da Web, onde um novo usuário pode ver orientações detalhadas sobre como configurar seu aplicativo com o Microsoft Teams.  Isso é para garantir que um novo usuário não seja bloqueado ao tentar o aplicativo pela primeira vez.
* A funcionalidade de entrada/saída deve funcionar em clientes móveis. Verifique se você está usando o [Microsoft Teams SDK](https://www.npmjs.com/package/@microsoft/teams-js) versão 1.4.1 ou posterior.

Para obter informações adicionais sobre autenticação, consulte:

* [Documentação de autenticação](../../../authentication/authentication.md)
* [Exemplo de autenticação de bot no nó](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
* [Exemplo de autenticação de guia no nó](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Autenticação de guia/bot no/.NET C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

### <a name="9989-response-times-must-be-reasonable"></a>Os tempos de resposta &#9989; devem ser razoáveis

* **Guias**. Se uma resposta a uma ação levar mais de três segundos, você deverá fornecer um aviso ou mensagem de carregamento.
* **Bots**. Uma resposta a um comando de usuário deve ocorrer dentro de dois segundos. Se for necessário processamento maior, seu aplicativo deverá exibir um indicador de digitação.
* **Extensões de composição**. Uma resposta a um comando de usuário deve ocorrer dentro de cinco segundos.

> [!TIP]
> Certifique-se de que o aplicativo exibe um indicador de carregamento ou alguma forma de aviso quando o aplicativo está demorando mais do que o esperado para responder.

### <a name="9989-tab-content-must-not-have-excessive-chrome-or-layered-navigation"></a>O conteúdo da guia &#9989; não deve ter uma navegação em camadas ou cromo excessivo

* As guias devem fornecer conteúdo focalizado e evitar elementos de interface do usuário desnecessários. Em geral, isso geralmente se refere à navegação desnecessária/aninhada em camadas, uma interface do usuário estranha ou irrelevante ao lado do conteúdo ou qualquer link que leva o usuário a conteúdo não relacionado. Por exemplo, abaixo está um modo de exibição de guia que omite menus de navegação e apenas exibe o conteúdo principal:

![Modo de exibição da Web do SharePoint](../../../../assets/images/faq/web-sp.png)  
![Exibição da guia do SharePoint](../../../../assets/images/faq/tab-sp.png)

* As guias devem ter natureza clara e não incluir a navegação complexa.
* As guias de canal que têm recursos de edição complexos no aplicativo devem abrir o modo de exibição editor em uma janela múltipla, e não uma guia.
* As guias de canal não devem fornecer uma barra de aplicativos com ícones no trilho esquerdo que estejam em conflito com a navegação do teams principal.
* As guias não devem apresentar uma barra de aplicativos com ícones no trilho esquerdo que entram em conflito com a navegação do teams principal.
* Guias com recursos de edição complexos no aplicativo devem abrir o modo de exibição editor em uma janela múltipla, e não na guia.
* Se houver várias opções de exibição, considere ter um menu de configuração de tabulação para o usuário escolher. Por exemplo, em vez de incorporar um menu dentro da guia, coloque o menu na página de configuração para que o modo de exibição de tabulação real seja limpo e focado.
* Inclua uma guia *ajuda* como uma guia estática para avisar os usuários sobre como configurar, inscrever e usar o aplicativo.
* Inclua uma guia de *configurações* disponível no cabeçalho do aplicativo.

![Página de configuração de grande ideia](../../../../assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>A configuração da guia &#9989; deve acontecer na tela configuração

* A tela configuração deve explicar claramente o valor da experiência e como configurar a guia.
* O processo de configuração sempre deve fornecer uma maneira para que os usuários continuem não se desativam da experiência do usuário. Por exemplo, não mostre uma placa vazia após o usuário ter configurado a guia
* O processo de entrada do usuário deve fazer parte do processo de configuração e deve ser concluído na interface do usuário da guia. Depois que o usuário tiver concluído a configuração e carregado sua guia, nenhuma ação adicional deverá ser necessária.
* Não mostrar toda a sua página da Web na janela pop-up configuração de entrada.
* Um usuário deve sempre ser capaz de concluir a experiência de configuração, mesmo que não possa encontrar imediatamente o conteúdo que está procurando.
* A experiência de configuração deve fornecer opções para que o usuário encontre o conteúdo, fixe uma URL ou crie um novo conteúdo se ele não existir.
* A experiência de configuração deve permanecer no contexto do Microsoft Teams. O usuário não deve ter que sair da experiência de configuração para criar conteúdo e, em seguida, retornar ao Teams para fixá-lo.
* Use a área de visor disponível de forma eficiente. Não desperdice o uso de logotipos grandes dentro da configuração pop up

![O OneNote permite que os usuários colem um link do OneNote em não é possível encontrar anotações](../../../../assets/images/faq/tab-onenote-config.png)

![Os usuários sempre podem criar um novo plano no Planner, caso não haja nenhum existente](../../../../assets/images/faq/tab-planner-config.png)

![O SharePoint também permite que o usuário Cole diretamente um link do SharePoint](../../../../assets/images/faq/tab-sp-config.png)

### <a name="9989-bots-must-always-be-responsive-and-fail-gracefully"></a>Os bots de &#9989; devem sempre ser responsivos e falhar normalmente

O bot deve ser responsivo para qualquer comando e não para o usuário. Aqui estão algumas dicas para ajudar seu bot a responder de forma inteligente aos usuários:

* **Usar listas de comandos**. Analisar a entrada do usuário ou prever a intenção do usuário é difícil. Em vez de permitir que os usuários adivinhem o que o seu bot pode fazer, forneça uma lista de comandos que seu bot entenda.

![Lista de comandos de fluxo](../../../../assets/images/faq/flow-bot.png)

* **Incluir um comando help**. É provável que os usuários digitem "ajuda" quando forem perdidos ou quando o bot não responder conforme o esperado. Inclua um comando help que descreva como o valor do aplicativo será experiente em todos os comandos válidos.

![Comando Flow Help](../../../../assets/images/faq/flow-help.png)

* **Inclua o conteúdo da ajuda ou orientações quando seu bot for perdido**. Quando o bot não entende a entrada do usuário, ele deve sugerir uma ação alternativa. Por exemplo, *"Eu não entendo. Digite "ajuda" para obter mais informações. "* Não responda com uma mensagem de erro ou simplesmente, *"não compreendo"*. Use essa oportunidade para ensinar seus usuários.

* **Use cartões adaptáveis e módulos de tarefas para tornar sua resposta de bot clara e acionável** 
 [Cartões adaptáveis com botões que chamam módulos de tarefa](/task-modules-and-cards/task-modules/task-modules-bots) aprimoram a experiência do usuário do bot. Esses cartões e botões são mais fáceis de usar em um dispositivo móvel, em oposição ao usuário que está digitando os comandos. Também as respostas de bot não devem ser textuais com texto longo. Os bots devem fazer uso de cartões adaptáveis & módulos de tarefas em vez de interface de usuário baseada em chat de conversa e respostas de texto demoradas

* **Considere todos os escopos**. Certifique-se de que o bot forneça respostas apropriadas quando for mencionado ( `@*botname*` ) em um canal e em conversas pessoais. Se o seu bot não fornecer um contexto significativo dentro do escopo pessoal ou do Teams, desabilite esse escopo por meio do manifesto. (Consulte o `bots` bloco na [referência do esquema de manifesto do Microsoft Teams](../../../../resources/schema/manifest-schema.md#bots).)

* **Incluir equipe, chat de grupo ou conversa 1:1**. As notificações de bot devem incluir uma equipe, um chat de grupo ou uma conversa de um-para-um com conteúdo relevante para o público.

* Não **envie dados confidenciais**. Os bots não devem enviar dados confidenciais para uma equipe, um chat de grupo ou uma conversa 1:1, onde há uma audiência que não deve ser capaz de exibir esses dados

* **Forneça uma mensagem de boas-vindas**. O bot deve fornecer uma mensagem de boas-vindas do FRE que inclui um tutorial interativo com cartões de carrossel ou botões "Experimente", para incentivar o contrato.

### <a name="9989-personal-bots-must-always-send-a-welcome-message-on-first-launch"></a>&#9989; bots pessoais sempre devem enviar uma mensagem de boas-vindas na primeira inicialização

Uma mensagem de boas-vindas é a melhor maneira de definir o Tom para seu bot pessoal/chat. Esta é a primeira interação de um usuário com o bot. Uma boa mensagem de boas-vindas pode incentivar o usuário a continuar a explorar o aplicativo. Se a mensagem de boas-vindas ou introdutória for confusa ou innítida, os usuários não verão o valor do aplicativo imediatamente e perderão os interesses.
Consulte a seção abaixo para ver os requisitos de mensagem de boas-vindas.

> [!Note]
> Uma mensagem de boas-vindas é opcional para um bot de canal.

### <a name="welcome-message-requirements"></a>Requisitos de mensagem de boas-vindas

* Inclua uma proposta de valor com o Tour de boas-vindas.
* Fornecer orientação de avanço para usar o aplicativo.
* Incluir orientações sobre como se inscrever e configurar seu aplicativo
* Apresente texto fácil de ler e uma caixa de diálogo direta, de preferência um cartão com um botão de Tour de boas-vindas acionável que carrega um módulo de tarefa.
* Mantenha a caixa de diálogo simples e usável com botões e cartões — Evite texto longo, caixa de diálogo informativa.
* Inclua cartões e botões adaptáveis para tornar a mensagem de boas-vindas mais utilizável.
* Invocar a mensagem de boas-vindas com um ping, não dois ou mais pings simultâneos.
* Uma mensagem de boas-vindas só deve ser exibida para o usuário que configurou o aplicativo, de preferência em um bate-papo pessoal 1:1.
* Os aplicativos pessoais sempre devem fornecer uma mensagem de boas-vindas a um usuário.
* Nunca envie um chat pessoal para todos os membros da equipe-isso é considerado spam.
* Nunca envie a mensagem de boas-vindas mais de uma vez. Repetir a mesma mensagem de boas-vindas por intervalos regulares não é permitida e é considerada como spam.

#### <a name="avoid-welcome-message-spamming"></a>Evitar o spam de mensagens de boas-vindas

* **Mensagem do canal por bot**. Não enviar spam a usuários criando novas postagens de chat separadas. Crie uma única postagem de thread com respostas no mesmo thread.
* **Chat pessoal por bot**. Não envie várias mensagens. Envie uma mensagem com informações completas. Repetir a mesma mensagem de boas-vindas por intervalos regulares não é permitida e é considerada como spam.

#### <a name="notification-only-bot-welcome-messages"></a>Mensagens de boas-vindas do bot somente de notificação

Notificações apenas bots devem enviar uma mensagem de boas-vindas que inclui uma mensagem que se comunica, *"Eu sou um bot somente para notificação e não conseguirá responder a seus chat"*.

#### <a name="welcome-messages-in-the-personal-scope"></a>Mensagens de boas-vindas no escopo pessoal

* **Torne sua mensagem concisa e informativa**.  Provavelmente, a experiência do usuário com o e o conhecimento do seu aplicativo irão variar. Um usuário pode ter usado seu aplicativo em outra plataforma ou não sabe nada sobre seu aplicativo. Você deseja adaptar sua mensagem a todos os públicos e em algumas frases explique o que o seu bot faz e as maneiras de interagir com ele. Você também deve explicar o valor do aplicativo e como os usuários se beneficiarão de usá-lo.
![Bot e bot dinning](../../../../assets/images/faq/cafe-bot.png)

* **Tornar sua mensagem acionável**. Considere a primeira coisa que você deseja que os usuários façam após instalar seu aplicativo. Há um comando interessante que ele deve tentar? Há outra experiência de integração que precisa saber? Eles precisam entrar? Você pode adicionar ações em um cartão adaptável ou fornecer exemplos específicos, como *"Experimente fazer isso...."*, *"é isso que eu posso fazer..."*.

#### <a name="welcome-messages-in-the-teamchannel--scope"></a>Mensagens de boas-vindas no escopo de equipe/canal

As coisas são um pouco diferentes quando o bot é adicionado pela primeira vez a um canal. Normalmente, você não deve enviar uma mensagem 1:1 para todas as pessoas da equipe, mas o bot pode enviar uma mensagem de boas-vindas no canal.

### <a name="9989-mobile-responsiveness-no-direct-upsell-or-payment"></a>&#9989; capacidade de resposta móvel, sem vendas diretas ou pagamentos

* Suas guias, cartões adaptáveis, mensagens de bot e conteúdo nos módulos de tarefas devem ser responsivos para uma variedade de tamanhos de telas de dispositivos móveis.
* Os aplicativos que dão suporte ao iOS devem estar totalmente funcionais no dispositivo iPad mais recente usando a versão mais recente do iOS.
* Não deve incluir referências diretas para compras no aplicativo, ofertas de avaliação, ofertas para versões pagas ou links para qualquer loja online, onde os usuários podem comprar ou adquirir outros conteúdos, aplicativos ou suplementos do aplicativo do Microsoft Teams no sistema operacional móvel (Android, iOS).
* A versão iOS ou Android do suplemento não deve mostrar qualquer interface do usuário ou idioma ou um link para outros aplicativos, suplementos ou sites que pedem que o usuário pague.
* A política de privacidade associada e as páginas de termos de uso também devem ser livres de qualquer UI de comércio ou links de armazenamento.

### <a name="9989-do-not-post-sensitive-data-to-an-audience-not-intended-to-view-the-data"></a>&#9989; não postar dados confidenciais para uma audiência não destinado a exibir os dados

O aplicativo do Microsoft Teams não deve postar dados confidenciais, como instrumento de cartão de crédito/pagamento financeiro, informações de identificação pessoal (PIN), integridade ou rastreamento de contato para uma audiência que não se destina a exibir esses dados.

### <a name="9989-do-not-transmit-financial-payment-details-or-complete-financial-transactions-via-your-teams-app"></a>&#9989; não transmite detalhes de pagamento financeiro ou transações financeiras completas por meio de seu aplicativo do teams

* O aplicativo do Microsoft Teams não deve solicitar que os usuários façam um pagamento diretamente dentro da interface do teams
* Os aplicativos podem não transmitir detalhes do instrumento financeiro através do usuário na interface do aplicativo. Os aplicativos só poderão transmitir links para serviços de pagamento seguro para os usuários se isso for divulgado nos termos de uso do aplicativo, política de privacidade e qualquer página de perfil ou site para o aplicativo antes que um usuário concorde em usar o aplicativo.

### <a name="9989-clear-warning-before-downloading-any-files-or-executable-exe-into-a-users-environment"></a>&#9989; limpar aviso antes de baixar arquivos ou executáveis ( `.exe` ) no ambiente de um usuário

Avise os usuários antes que seu aplicativo Baixe qualquer arquivo ou executável ( `.exe`  ) no computador ou no ambiente do usuário.

### <a name="9989-messaging-extensions-should-provide-help-text-and-be-easy-to-read"></a>&#9989; extensões de mensagens devem fornecer texto de ajuda e ser fácil de ler

* A extensão de mensagens baseada em pesquisa deve fornecer texto de ajuda sobre como Pesquisar com eficiência (por exemplo, mostrar a entrada de exemplos).
* Os módulos de tarefa devem incluir um ícone e um nome curto em que eles estão contidos ou criados no aplicativo.
* Os executáveis de extensão de mensagem `@mention` devem ser claros, fáceis de entender e fáceis de ler.
![Extensão de mensagem](../../../../assets/images/faq/message-extension.png)

> [!div class="nextstepaction"]
> [Saiba mais sobre as políticas de aprovação do teams app](/legal/marketplace/certification-policies#1140-teams)
