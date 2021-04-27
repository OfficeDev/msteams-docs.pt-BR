---
title: Dicas de envio de aplicativo e casos com falha frequente
description: descreve dicas para um envio bem-sucedido do Armazenamento do Teams e os envios de motivos comuns falham
ms.topic: reference
localization_priority: Normal
ms.author: lajanuar
keywords: dicas de envio de aplicativo com frequência diretrizes de validação de casos com falha
ms.openlocfilehash: a5e03f6ac7afb949cb94824fde3514a14869b291
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019913"
---
# <a name="tips-for-a-successful-microsoft-teams-app-submission"></a>Dicas para um envio bem-sucedido de aplicativos do Microsoft Teams

Este artigo aborda motivos comuns para a validação de falha dos aplicativos enviados. Embora não se pretenda ser uma lista exaustiva de todos os possíveis problemas com seu aplicativo, seguir este guia aumentará a probabilidade de o envio do aplicativo passar pela primeira vez. Consulte [Políticas de certificação do marketplace](/legal/marketplace/certification-policies) comercial para uma lista extensa de políticas de validação.

>[!NOTE]
>**[A Seção 1140](/legal/marketplace/certification-policies#1140-teams)** é específica do Microsoft Teams e a **[subseção 1140.4](https://docs.microsoft.com/legal/marketplace/certification-policies#11404-functionality)** atende aos requisitos de funcionalidade para aplicativos do Teams.

## <a name="validation-guidelines--most-failed-test-cases"></a>Diretrizes de validação & a maioria dos casos de teste com falha

### <a name="9989-general-considerations"></a>&#9989; considerações gerais

Consulte também [Seção 100 — Geral](/legal/marketplace/certification-policies#100-general)

* Verifique se você está usando a versão 1.4.1 ou posterior do [SDK](https://www.npmjs.com/package/@microsoft/teams-js)do Microsoft Teams.
* Não faça alterações em seu aplicativo enquanto o processo de validação estiver em andamento. Isso exigirá uma revalidação completa do seu aplicativo.
* Seu aplicativo não deve parar de responder, terminar inesperadamente ou conter erros de programação. Se ocorrer um problema, seu aplicativo deverá falhar e fornecer informações válidas para o encaminhamento para o usuário.
* Seu aplicativo não deve baixar, instalar ou iniciar automaticamente qualquer código executável no ambiente do usuário. Todos os downloads devem buscar permissão explícita do usuário.
* Qualquer material associado à sua experiência, como descrições e documentação de suporte, deve ser preciso. Use ortografia, capitalização, pontuação e gramática corretas em suas descrições e materiais.
* Forneça informações de ajuda e suporte. É altamente recomendável que seu aplicativo inclua uma ajuda ou um link de perguntas frequentes para a experiência do usuário de primeira. Para todos os aplicativos pessoais, recomendamos fornecer sua página de ajuda como uma guia pessoal para uma melhor experiência do usuário.
* Todos os aplicativos devem ter  um tour  visual, como Fazer um Tour ou um Guia de Aplicativo em sua tela de configuração que fale sobre os recursos do aplicativo e a integração necessária nos seguintes locais:
    * A página de listagem da loja (Long Description).
    * Tela de configuração de tabulação.
    * Mensagem de boas-vindas para um bot.
    * Metadados de origem do aplicativo.
    * Tela de configuração do conector.

* O tour visual pode ser um vídeo, captura de tela, um link para uma guia estática com detalhes do aplicativo. Todas essas referências devem estar no ambiente do Teams.

    ![Exemplo de aplicativo 1 ](../../../../assets/images/faq/Sampleapp1.png) ![ exemplo de aplicativo 2](../../../../assets/images/faq/Sampleapp2.png)

* Incremente o número da versão do aplicativo no manifesto se você fizer alterações de manifesto no envio.
* O aplicativo não deve tirar os usuários do Teams para cenários principais do usuário. Os destinos de link em aplicativos não devem ser link para um navegador externo. Os destinos de link devem vincular aos elementos div contidos no Teams, por exemplo, módulos de tarefas e guias. 
* O uso de módulos de tarefas ou guias é sugerido para exibir informações aos usuários no Teams.
* Todos os cenários principais e não essenciais devem ser concluídos no ambiente do Teams, exceto por:
  * Política de privacidade
  * Termos de Uso (TOU)
  * Link do site
  * Processo de inscrever-se

* Aplicativos pessoais permitem que os usuários compartilhem conteúdo de uma experiência de aplicativo pessoal com outros membros da equipe.

### <a name="9989-provide-a-clear-and-simple-sign-in-sign-out-and-sign-up-experience"></a>&#9989; fornecer uma experiência clara e simples de entrar, entrar e inscrever-se

Consulte também [Seção 1100.5 — Controle do cliente](/legal/marketplace/certification-policies#11005-customer-control)

* Se o aplicativo ou o seu add-in depender de contas ou serviços externos, a experiência de login, de saída e de assinatura deve ser aparente e acessível em todos os recursos em seu aplicativo.
* Se houver uma opção de login explícita fornecida ao usuário, deverá haver uma opção de saída correspondente (mesmo se o aplicativo estiver usando autenticação [silenciosa](../../../../tabs/how-to/authentication/auth-silent-aad.md)).
* A opção de saída só deve tirar o usuário da funcionalidade do aplicativo e não sair do cliente do Teams.
* No mínimo, a opção de saída deve fazer com que o usuário saia dos mesmos recursos acessados com a opção de login. Por exemplo, se a opção de login incluir a extensão de mensagens e a guia, a opção de saída deverá incluir a extensão de mensagens e a guia.

* Certifique-se de que sempre haja uma maneira de reverter os seguintes comportamentos (ou semelhantes:
  * Entrar => sair.
  * Vincular uma conta/serviço => desvincular uma conta/serviço.
  * Conectar uma conta/serviço => desconectar uma conta/serviço.
  * Autorizar uma conta/serviço => desautorizar/negar uma conta/serviço.
  * Registrar uma conta/serviço => deregister/cancelar a assinatura de uma conta/serviço.
* Se seu aplicativo exigir uma conta ou serviço, você deve fornecer uma maneira para o usuário se inscrever ou criar uma solicitação de inscrever-se. Uma exceção pode ser concedida se seu aplicativo exigir uma licença para usar. Nesses cenários, forneça instruções claras para um novo usuário se inscrever.
* Forneça orientações claras sobre o encaminhamento para um novo usuário sobre como se inscrever para usar seus serviços de aplicativo. Se um link de assinatura pronto não estiver disponível, forneça orientações precisas nas seguintes áreas:

> [!div class="checklist"]
>
> * na seção descrição do aplicativo.
> * na mensagem de boas-vindas do aplicativo.
> * na mensagem de ajuda do aplicativo.
> * na janela em que você pede a um usuário para entrar em seus serviços.

* Aplicativos sem um fluxo de inscrições fácil também devem incluir uma guia de ajuda ou um link para uma página da Web, onde um novo usuário pode ver orientações detalhadas sobre como configurar seu aplicativo do Teams. Forneça informações detalhadas para garantir que um novo usuário não seja bloqueado ao tentar seu aplicativo pela primeira vez.
* A funcionalidade de entrar e sair deve funcionar em clientes móveis. Certifique-se de usar o [SDK do Microsoft Teams](https://www.npmjs.com/package/@microsoft/teams-js) versão 1.4.1 ou posterior.

Para obter informações adicionais sobre autenticação, consulte:

* [Documentação de autenticação](../../../authentication/authentication.md)
* [Exemplo de autenticação bot no Nó](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
* [Exemplo de autenticação de tabulação no Nó](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Autenticação de tabulação/bot no C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

### <a name="9989-response-times-must-be-reasonable"></a>&#9989; os tempos de resposta devem ser razoáveis

* **Guias**. Se uma resposta a uma ação levar mais de três segundos, você deverá fornecer uma mensagem de carregamento ou um aviso.
* **Bots**. Uma resposta a um comando do usuário deve ocorrer em dois segundos. Se o processamento mais longo for necessário, seu aplicativo deverá exibir um indicador de digitação.
* **Redação de extensões**. Uma resposta a um comando do usuário deve ocorrer dentro de cinco segundos.

> [!TIP]
> Certifique-se de que seu aplicativo exibe um indicador de carregamento ou alguma forma de aviso quando o aplicativo estiver demorando mais do que o esperado para responder.

### <a name="9989-tab-content-must-not-have-excessive-chrome-or-layered-navigation"></a>&#9989; conteúdo tab não deve ter navegação excessiva em camadas ou cromadas

* As guias devem fornecer conteúdo focado e evitar elementos de interface do usuário desnecessários. Isso geralmente se refere a navegação aninhada ou em camadas desnecessária, uma interface do usuário externa ou irrelevante ao lado do conteúdo ou quaisquer links que levam o usuário ao conteúdo não relacionado. Por exemplo, o modo de exibição de tabulação a seguir omite menus de navegação e mostra apenas o conteúdo principal:

![Exibição da Web do SharePoint](../../../../assets/images/faq/web-sp.png)  
![Exibição de guia do SharePoint](../../../../assets/images/faq/tab-sp.png)

* As guias devem ter natureza leve e não incluir navegação complexa.
* As guias de canal com recursos complexos de edição dentro do aplicativo devem abrir o modo de exibição do editor em uma janela com várias janelas, em vez de uma guia.
* As guias de canal não devem fornecer uma barra de aplicativos com ícones no trilho esquerdo que conflitam com a navegação principal do Teams.
* As guias não devem apresentar uma barra de aplicativos com ícones no trilho esquerdo que conflitam com a navegação principal do Teams.
* Guias com recursos complexos de edição dentro do aplicativo devem abrir o modo de exibição do editor em uma janela com várias janelas, em vez de na guia.
* Se houver várias opções de exibição, considere ter um menu de configuração de tabulação para o usuário escolher. Por exemplo, em vez de incorporar um menu dentro da guia, coloque o menu na página de configuração para que o modo de exibição de tabulação real seja limpo e focado.
* Inclua uma guia *Ajuda como* uma guia estática para aconselhar os usuários a configurar, inscrever-se e usar seu aplicativo.
* Inclua uma *guia Configurações* que está disponível no header do aplicativo.

![Página de configuração de ampla ideia](../../../../assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>&#9989; configuração tab deve acontecer na tela de configuração

* A tela de configuração deve explicar claramente o valor da experiência e como configurar a guia.
* O processo de configuração sempre deve fornecer uma maneira para que os usuários continuem e não terminem a experiência do usuário. Por exemplo, não mostre uma placa vazia depois que o usuário configurou a guia.
* O processo de entrada do usuário deve fazer parte do processo de configuração. Certifique-se de conclua-lo na interface do usuário da guia. Depois que o usuário concluiu a configuração e carregou a guia, nenhuma outra ação é necessária.
* Não mostre toda a página da Web na janela pop-up de configuração de entrada.
* Um usuário sempre deve ser capaz de concluir a experiência de configuração, mesmo que não consiga encontrar imediatamente o conteúdo que está procurando.
* A experiência de configuração deve fornecer opções para o usuário encontrar seu conteúdo, fixar uma URL ou criar novo conteúdo se ele não existir.
* A experiência de configuração deve permanecer no contexto do Teams. O usuário não deve ter que deixar a experiência de configuração para criar conteúdo e, em seguida, retornar ao Teams para fixá-lo.
* Use a área do modo de exibição disponível com eficiência. Não desperdiçou o uso de logotipos enormes dentro da configuração pop-up.

![O OneNote permite que os usuários colarem um link do OneNote caso as anotações não possam ser encontradas](../../../../assets/images/faq/tab-onenote-config.png)

![Os usuários sempre podem criar um novo plano no planejador caso não haja nenhum plano existente](../../../../assets/images/faq/tab-planner-config.png)

![O SharePoint também permite que o usuário colar diretamente um link do SharePoint](../../../../assets/images/faq/tab-sp-config.png)

### <a name="9989-tabs-in-channel---member-access"></a>&#9989; guias no canal - Acesso para membros

* Uma guia configurada por um membro em um escopo de canal deve estar acessível aos outros membros sem precisar buscar permissões do membro que configurou a guia.
* O aplicativo deve fornecer as opções de gerenciamento de permissão antecipadamente se a guia for para uso privado ou restrito ou exigir qualquer permissão do membro que configurou a guia.

### <a name="9989-bots-must-always-be-responsive-and-fail-gracefully"></a>&#9989; bots sempre devem ser responsivos e falhar normalmente

Seu bot deve estar respondendo a qualquer comando e não in-locar o usuário. Aqui estão algumas dicas para ajudar seu bot a responder de forma inteligente aos usuários:

* **Usar listas de comandos**. Analisar a entrada do usuário ou prever a intenção do usuário é difícil. Em vez de permitir que os usuários adivinharem o que seu bot pode fazer, forneça uma lista de comandos que seu bot entende.

![Lista de comandos de fluxo](../../../../assets/images/faq/flow-bot.png)

* **Inclua um comando de ajuda**. Os usuários provavelmente digitarão "Ajuda" quando perderem ou quando o bot não responder conforme esperado. Inclua um comando de ajuda que descreve como o valor do aplicativo será experimentado juntamente com todos os comandos válidos.

![Comando de ajuda de fluxo](../../../../assets/images/faq/flow-help.png)

* **Inclua conteúdo de ajuda ou orientações quando seu bot for perdido**. Quando o bot não consegue entender a entrada do usuário, ele deve sugerir uma ação alternativa. Por exemplo, *"Desculpe, não consigo entender. Digite "ajuda" para obter mais informações."* Não responda com uma mensagem de erro ou *simplesmente, "Não estou entendendo".*

### <a name="9989-help-command-response"></a>&#9989; resposta de comando da Ajuda

* O Comando de Ajuda deve ser preciso e as respostas do aplicativo devem estar em um formato de cartão adaptável com um conteúdo a ação para pelo menos seis comandos.
* Se um aplicativo tiver menos de seis comandos, verifique se todos os comandos estão presentes no cartão adaptável.

  ![Exemplo de comando de ajuda](../../../../assets/images/faq/helpcommand.png)

* **Use cartões adaptáveis e módulos de tarefa para tornar a resposta do bot clara e a actionable** 
 [Cartões adaptáveis com botões invocando módulos](/task-modules-and-cards/task-modules/task-modules-bots) de tarefa aprimoram a experiência do usuário do bot. Esses cartões e botões são mais fáceis de usar em um dispositivo móvel, em vez do usuário digitar os comandos. Além disso, as respostas de bot não devem ser textuais com texto longo. Os bots devem usar cartões adaptáveis e módulos de tarefa em vez de interfaces de usuário baseadas em chat de conversa e respostas de texto longas.

* **Pense em todos os escopos.** Certifique-se de que seu bot fornece respostas apropriadas quando mencionado ( `@*botname*` ) em um canal e em conversas pessoais. Se o bot não fornecer contexto significativo no escopo pessoal ou de equipes, desabilite esse escopo por meio do manifesto. (Consulte o bloco na referência de esquema de manifesto `bots` [do Microsoft Teams](../../../../resources/schema/manifest-schema.md#bots).)

* **Inclua equipe, chat em grupo ou conversa 1:1.** As notificações de bot devem incluir uma equipe, um bate-papo em grupo ou uma conversa um para um com conteúdo relevante para sua audiência.

* **Não pressione dados confidenciais.** Os bots não devem empurrar dados confidenciais para uma equipe, um chat em grupo ou uma conversa 1:1, onde há uma audiência que não deve exibir esses dados.

* **Forneça uma mensagem de boas-vindas**. Bot deve fornecer uma mensagem de boas-vindas FRE que inclui um tutorial interativo com cartões de carrossel ou botões "experimente", para incentivar o envolvimento.

### <a name="9989-personal-bots-must-always-send-a-welcome-message-on-first-launch"></a>&#9989; os bots pessoais sempre devem enviar uma mensagem de boas-vindas na primeira iniciação

Uma mensagem de boas-vindas é a melhor maneira de definir o tom do bot de chat pessoal. Esta é a primeira interação que um usuário tem com o bot. Uma boa mensagem de boas-vindas pode incentivar o usuário a continuar explorando o aplicativo. Se a mensagem de boas-vindas ou introdutório for confusa ou não clara, os usuários não verão o valor do aplicativo imediatamente e perderão o interesse.
Consulte a seção a seguir para requisitos de mensagem de boas-vindas:

> [!Note]
> Uma mensagem de boas-vindas é opcional para um bot de canal.

### <a name="welcome-message-requirements"></a>Requisitos de mensagem de boas-vindas

* Inclua uma proposta de valor com o tour de boas-vindas.
* Forneça orientações de avanço para o uso do aplicativo.
* Inclua orientações sobre como se inscrever e configurar seu aplicativo.
* Apresente texto fácil de ler e diálogo direto — preferencialmente um cartão com um botão de visita de boas-vindas a ação que carrega um módulo de tarefa.
* Mantenha-a simples e acessível com botões e cartões — evite texto longo, diálogo conversativo.
* Inclua cartões e botões adaptáveis para tornar a mensagem de boas-vindas mais usável.
* Invocar a mensagem de boas-vindas com um ping, não dois ou mais pings simultâneos.
* Uma mensagem de boas-vindas só deve ser mostrada ao usuário que configurou o aplicativo, preferencialmente em um chat pessoal 1:1.
* Aplicativos pessoais sempre devem fornecer uma mensagem de boas-vindas a um usuário.
* Nunca envie um chat pessoal para todos os membros da equipe; ele é considerado spam.
* Nunca envie a mensagem de boas-vindas mais de uma vez. Repetir a mesma mensagem de boas-vindas em intervalos regulares não é permitido e é considerado spam.

#### <a name="avoid-welcome-message-spamming"></a>Evitar spam de mensagens de boas-vindas

* **Mensagem de canal por bot**. Não spam usuários criando novas postagens de chat separadas. Crie uma única postagem de thread com respostas no mesmo thread.
* **Chat pessoal por bot**. Não envie várias mensagens. Envie uma mensagem com informações completas. Repetir a mesma mensagem de boas-vindas em intervalos regulares não é permitido e é considerado spam.

#### <a name="notification-only-bot-welcome-messages"></a>Mensagens de boas-vindas de bot somente notificação

Os bots somente notificação devem enviar uma mensagem de boas-vindas que inclui um transporte de mensagem: "Sou um bot somente notificação e não consigo responder aos *seus chats"*.

#### <a name="welcome-messages-in-the-personal-scope"></a>Mensagens de boas-vindas no escopo pessoal

   * **Tornar sua mensagem concisa e informativa**. A experiência do usuário e o conhecimento do seu aplicativo variam. Um usuário pode ter usado seu aplicativo em outra plataforma ou não saber nada sobre seu aplicativo. Você deseja adaptar sua mensagem a todas as audiências e em algumas frases explica o que seu bot faz e as maneiras de interagir com ela. Você também deve explicar o valor do aplicativo e como os usuários se beneficiarão de usá-lo.
![Bot Café e Dinning](../../../../assets/images/faq/cafe-bot.png)

* **Tornar sua mensagem a actionable**. Pense na primeira coisa que você deseja que os usuários faça depois de instalar seu aplicativo. Há um comando legal que eles devem tentar? Há outra experiência de integração que eles devem saber? Eles precisam entrar? Você pode adicionar ações em um cartão adaptável ou fornecer exemplos específicos como *"Tente perguntar...."*, "Isso é o *que posso fazer..."*.

#### <a name="welcome-messages-in-the-team-or-channel--scope"></a>Mensagens de boas-vindas no escopo de equipe ou canal

As coisas são um pouco diferentes quando o bot é adicionado pela primeira vez a um canal. Normalmente, você não deve enviar uma mensagem 1:1 para todos na equipe, mas o bot pode enviar uma mensagem de boas-vindas no canal.

### <a name="9989-mobile-responsiveness-no-direct-upsell-or-payment"></a>&#9989; capacidade de resposta móvel, nenhum upsell direto ou pagamento

* Suas guias, cartões adaptáveis, mensagens de bot e conteúdo em módulos de tarefas devem ser responsivos para uma variedade de tamanhos de telas de dispositivo móvel.
* Os aplicativos que suportam o iOS devem estar totalmente funcionais no dispositivo iPad mais recente usando a versão mais recente do iOS.
* Não deve incluir referências diretas a compras no aplicativo, ofertas de avaliação, ofertas para versões pagas ou links para qualquer loja online em que os usuários possam comprar ou adquirir outros conteúdos, aplicativos ou complementos do seu aplicativo do Teams no sistema operacional móvel (Android, iOS).
* A versão iOS ou Android do complemento não deve mostrar nenhuma interface do usuário ou idioma ou link para quaisquer outros aplicativos, complementos ou site que peçam ao usuário para pagar.
* As páginas de Política de Privacidade e Termos de Uso associadas também devem estar livres de qualquer interface do usuário do comércio ou links da Loja.

### <a name="9989-do-not-post-sensitive-data-to-an-audience-not-intended-to-view-the-data"></a>&#9989; Não poste dados confidenciais para uma audiência que não se destina a exibir os dados

Seu aplicativo do Teams não deve postar dados confidenciais, como cartão de crédito ou instrumento de pagamento financeiro, PIN (Personal Identifiable Information), health ou contact tracing information to an audience not intended to view that data.

### <a name="9989-do-not-transmit-financial-payment-details-or-complete-financial-transactions-via-your-teams-app"></a>&#9989; Não transmita detalhes de pagamento financeiros ou conclua transações financeiras por meio do aplicativo do Teams

* Seu aplicativo do Teams não deve solicitar que os usuários façam um pagamento diretamente na interface do Teams.
* Os aplicativos podem não transmitir detalhes do instrumento financeiro por meio do usuário na interface do aplicativo. Os aplicativos só poderão transmitir links para serviços de pagamento seguros para os usuários se isso for divulgado nos Termos de Uso, Política de Privacidade e qualquer página de perfil ou site do aplicativo antes que um usuário concorde em usar o aplicativo.

### <a name="9989-clear-warning-before-downloading-any-files-or-executable-exe-into-a-users-environment"></a>&#9989; Limpar aviso antes de baixar quaisquer arquivos ou executáveis ( `.exe` ) no ambiente de um usuário

Avise os usuários antes que seu aplicativo baixe arquivos ou executáveis ( )para o computador ou ambiente `.exe`  do usuário.

### <a name="9989-messaging-extensions-must-provide-help-text-and-be-easy-to-read"></a>&#9989; extensões de mensagens devem fornecer texto de ajuda e ser fácil de ler

* A extensão de mensagens baseada em pesquisa deve fornecer texto de ajuda sobre como pesquisar efetivamente (por exemplo, mostrar entrada de exemplo).
* Os módulos de tarefa devem incluir um ícone e um nome curto em que estão contidos ou criados a partir do aplicativo.
* Os executáveis de `@mention` extensão de mensagem devem ser claros, fáceis de entender e fáceis de ler.
![Extensão de mensagem](../../../../assets/images/faq/message-extension.png)

## <a name="m365-publisher-attestation"></a>Atestado do Editor M365

### <a name="9989-complete-the-publisher-attestation-in-partner-center"></a>&#9989; Concluir o Atestado do Publisher no Partner Center

* Consulte a [documentação do programa Detestação completa do](/microsoft-365-app-certification/docs/attestation) Publisher para obter mais detalhes.
* Siga as etapas na seção Fluxo de Trabalho de Atestado [do Publisher](/microsoft-365-app-certification/docs/userguide#3publisher-attestation-workflow) para concluir o processo de atestado do editor. Escreva no appcert@microsoft.com para qualquer dúvida.
* Consulte o guia [Solução de Problemas para](/azure/active-directory/develop/troubleshoot-publisher-verification) obter informações adicionais.
* Conclua o autoteste por meio do Partner Center. Preencha o Self-Assessment questionário em **Conformidade com Aplicativos.**

> [!div class="nextstepaction"]
> [Saiba mais sobre as políticas de aprovação de aplicativos do Teams](/legal/marketplace/certification-policies#1140-teams)
