---
title: Dicas de submissão de aplicativos e casos com frequência
description: descreve dicas para uma apresentação de loja de Teams bem sucedida e as submissões de razões comuns falham
ms.topic: reference
localization_priority: Normal
ms.author: lajanuar
keywords: dicas de submissão de aplicativos frequentemente falham diretrizes de validação de casos
ms.openlocfilehash: 50bbd2af3b4c834e2ac4776e1fc7db1d8bf45173
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565228"
---
# <a name="tips-for-a-successful-microsoft-teams-app-submission"></a>Dicas para uma apresentação bem-sucedida de aplicativos Microsoft Teams

>[!NOTE]
>Esta página será preterida até maio de 2021. Para obter mais informações sobre a publicação do seu aplicativo com sucesso, consulte as [diretrizes de validação de Teams armazenamento](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).

Este artigo aborda razões comuns que os aplicativos submetidos falham na validação. Embora não se destine a ser uma lista exaustiva de todos os problemas potenciais com o seu aplicativo, seguir este guia aumentará a probabilidade de que sua submissão de aplicativo passe pela primeira vez. Para obter mais informações, consulte [as políticas de certificação de marketplace comercial](/legal/marketplace/certification-policies) para uma extensa lista de políticas de validação.

>[!NOTE]
>**[A seção 1140](/legal/marketplace/certification-policies#1140-teams)** é específica para Microsoft Teams e **[a subseção 1140.4](/legal/marketplace/certification-policies#11404-functionality)** aborda os requisitos de funcionalidade para aplicativos Teams.

## <a name="validation-guidelines--most-failed-test-cases"></a>As diretrizes de validação & mais casos de teste com falha

### <a name="9989-general-considerations"></a>&#9989; Considerações gerais

* Certifique-se de que está usando a versão 1.4.1 ou posterior do [Microsoft Teams SDK](https://www.npmjs.com/package/@microsoft/teams-js).
* Não faça alterações no seu aplicativo enquanto o processo de validação estiver em andamento. Isso exigirá uma revalidação completa do seu aplicativo.
* Seu aplicativo não deve parar de responder, terminar inesperadamente ou conter erros de programação. Se ocorrer um problema, seu aplicativo deve falhar e fornecer informações válidas para o encaminhamento para o usuário.
* Seu aplicativo não deve baixar, instalar ou iniciar automaticamente qualquer código executável no ambiente do usuário. Todos os downloads devem buscar permissão explícita do usuário.
* Qualquer material que você associar à sua experiência, como descrições e documentação de suporte, deve ser preciso. Use a ortografia correta, a capitalização, a pontuação e a gramática em suas descrições e materiais.
* Forneça informações de ajuda e suporte. É altamente recomendável que seu aplicativo inclua um link de ajuda ou FAQ para a experiência do usuário de primeira linha. Para todos os aplicativos pessoais, recomendamos fornecer sua página de ajuda como uma guia pessoal para uma melhor experiência do usuário.
* Todos os aplicativos devem ter um passeio visual, como **o Take a Tour** ou um App **Guide** em sua tela de configuração que fala sobre os recursos do aplicativo e a integração necessária nos seguintes lugares:
    * A página de listagem da loja (Descrição Longa).
    * Tela de configuração da guia.
    * Mensagem de boas-vindas para um robô.
    * Metadados de fonte de aplicativo.
    * Tela de configuração do conector.

* O passeio visual pode ser um vídeo, captura de tela, um link para uma guia estática com detalhes do aplicativo. Todas essas referências devem estar dentro do ambiente Teams.

    ![Amostra app 1 ](../../../../assets/images/faq/Sampleapp1.png) ![ amostra app 2](../../../../assets/images/faq/Sampleapp2.png)

* Incremente o número da versão do aplicativo no manifesto se você fizer alterações manifestas no seu envio.
* O aplicativo não deve tirar os usuários de Teams para os principais cenários do usuário. Os alvos de link em aplicativos não devem vincular a um navegador externo. Os alvos de link devem vincular-se aos elementos div contidos dentro de Teams, por exemplo, módulos de tarefa e guias. 
* O uso de módulos ou guias de tarefas é sugerido para exibir informações aos usuários dentro de Teams.
* Todos os cenários centrais e não essenciais devem ser concluídos dentro do ambiente Teams, exceto por:
  * Política de privacidade
  * Termos de Uso (TOU)
  * Link do site
  * Processo de inscrição

* Aplicativos pessoais permitem que os usuários compartilhem conteúdo a partir de uma experiência de aplicativo pessoal com outros membros da equipe.

### <a name="9989-provide-a-clear-and-simple-sign-in-sign-out-and-sign-up-experience"></a>&#9989; Fornecer uma experiência clara e simples de login, aprovação e inscrição

* Se o seu aplicativo ou complemento depender de contas ou serviços externos, a experiência de login, login e inscrição deve ser aparente e acessível em todos os recursos do seu aplicativo.
* Se houver uma opção de login explícita fornecida ao usuário, deve haver uma opção de saída correspondente (mesmo que o aplicativo esteja usando [autenticação silenciosa](../../../../tabs/how-to/authentication/auth-silent-aad.md)).
* A opção de saída só deve tirar o usuário da capacidade do seu aplicativo e não sair do Teams cliente.
* No mínimo, a opção de login deve tirar o usuário dos mesmos recursos acessados com a opção de login. Por exemplo, se a opção de login incluir extensão de mensagens e guia, então a opção de saída de sinal deve incluir extensão de mensagens e guia.

* Certifique-se de que há sempre uma maneira de reverter os seguintes (ou similares) comportamentos:
  * Login => saída.
  * Vincule uma conta/serviço => desvincular uma conta/serviço.
  * Conexão uma conta/serviço => desconectar uma conta/serviço.
  * Autorizar uma conta/serviço => desautorizar/negar uma conta/serviço.
  * Cadastre uma conta/serviço => desregistrem/cancelar a assinatura de uma conta/serviço.
* Se o seu aplicativo exigir uma conta ou serviço, você deve fornecer uma maneira de o usuário se inscrever ou criar uma solicitação de inscrição. Uma exceção pode ser concedida se o seu aplicativo exigir uma licença para usar. Nesses cenários, forneça instruções claras para um novo usuário se inscrever.
* Forneça orientações claras sobre o caminho para um novo usuário sobre como se inscrever para usar seus serviços de aplicativo. Se um link de inscrição pronto não estiver disponível, forneça orientações precisas nas seguintes áreas:

> [!div class="checklist"]
>
> * dentro da seção de descrição do seu aplicativo.
> * na mensagem de boas-vindas do seu aplicativo.
> * na mensagem de ajuda do seu aplicativo.
> * na janela onde você pede a um usuário para fazer login em seus serviços.

* Os aplicativos sem um fluxo de inscrição fácil também devem incluir uma guia de ajuda ou link para uma página da Web, onde um novo usuário pode ver orientações detalhadas sobre a configuração de seu aplicativo Teams. Forneça informações detalhadas para garantir que um novo usuário não seja bloqueado ao experimentar seu aplicativo pela primeira vez.
* A funcionalidade de login e login deve funcionar em clientes móveis. Certifique-se de usar o Microsoft Teams versão [SDK](https://www.npmjs.com/package/@microsoft/teams-js) 1.4.1 ou posterior.

Para obter informações adicionais sobre autenticação, consulte:

* [Documentação de autenticação](../../../authentication/authentication.md)
* [Amostra de autenticação de bot em Node](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
* [Amostra de autenticação de guia em Node](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Autenticação de guia/bot em C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

### <a name="9989-response-times-must-be-reasonable"></a>&#9989; os tempos de resposta devem ser razoáveis

* **Guias**. Se uma resposta a uma ação levar mais de três segundos, você deve fornecer uma mensagem de carregamento ou aviso.
* **Bots**. Uma resposta a um comando de usuário deve ocorrer dentro de dois segundos. Se for necessário um processamento mais longo, o aplicativo deve exibir um indicador de digitação.
* **Compor extensões**. Uma resposta a um comando de usuário deve ocorrer dentro de cinco segundos.

> [!TIP]
> Certifique-se de que seu aplicativo exibe um indicador de carregamento ou algum tipo de aviso quando seu aplicativo está demorando mais do que o esperado para responder.

### <a name="9989-tab-content-must-not-have-excessive-chrome-or-layered-navigation"></a>&#9989; O conteúdo da guia não deve ter navegação excessiva e cromada ou em camadas

* As guias devem fornecer conteúdo focado e evitar elementos de interface do usuário desnecessários. Isso geralmente se refere a navegação aninhada ou em camadas desnecessária, uma interface do usuário ímvas ou irrelevantes ao lado do conteúdo ou quaisquer links que levem o usuário a conteúdo não relacionado. Por exemplo, a visualização da guia a seguir omite menus de navegação e só mostra o conteúdo principal:

![SharePoint visão web](../../../../assets/images/faq/web-sp.png)  
![SharePoint visualização da guia](../../../../assets/images/faq/tab-sp.png)

* As guias devem ser leves na natureza e não incluir navegação complexa.
* As guias de canal que possuem recursos complexos de edição dentro do aplicativo devem abrir a exibição do editor em uma janela de várias janelas em vez de uma guia.
* As guias do canal não devem fornecer uma barra de aplicativo com ícones no trilho esquerdo que entrem em conflito com a navegação principal Teams.
* As guias não devem apresentar uma barra de aplicativo com ícones no trilho esquerdo que conflitam com a principal navegação Teams.
* As guias que possuem recursos complexos de edição dentro do aplicativo devem abrir a exibição do editor em uma janela de várias janelas e não na guia.
* Se houver várias opções de exibição, considere ter um menu de guias para o usuário escolher. Por exemplo, em vez de incorporar um menu dentro da guia, coloque o menu na página de configuração para que a exibição real da guia seja limpa e focada.
* Por favor, inclua uma guia *Ajuda* como uma guia estática para aconselhar os usuários como configurar, se inscrever e usar seu aplicativo.
* Por favor, inclua uma guia *Configurações* que está disponível no cabeçalho do aplicativo.

![Página de configuração de ideia ampla](../../../../assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>&#9989; configuração da guia deve acontecer na tela de configuração

* A tela de configuração deve explicar claramente o valor da experiência e como configurar a guia.
* O processo de configuração deve sempre fornecer uma maneira para os usuários continuarem e não acabarem com a experiência do usuário. Por exemplo, não mostre uma placa vazia depois que o usuário tiver configurado a guia.
* O processo de login do usuário deve fazer parte do processo de configuração. Certifique-se de completá-lo na interface do usuário da tab. Depois que o usuário tiver concluído a configuração e carregado a guia, nenhuma ação adicional é necessária.
* Não mostre toda a sua página na web dentro da janela pop-up de configuração de login.
* Um usuário deve sempre ser capaz de terminar a experiência de configuração, mesmo que não consiga encontrar imediatamente o conteúdo que está procurando.
* A experiência de configuração deve fornecer opções para que o usuário encontre seu conteúdo, fixe uma URL ou crie um novo conteúdo se ele não existir.
* A experiência de configuração deve permanecer dentro do contexto Teams. O usuário não deve ter que deixar a experiência de configuração para criar conteúdo e, em seguida, retornar ao Teams para fixá-lo.
* Use a área de viewport disponível de forma eficiente. Não o desperdice usando logotipos enormes dentro da configuração.

![OneNote permite que os usuários colem um link de OneNote caso as notas não sejam encontradas](../../../../assets/images/faq/tab-onenote-config.png)

![Os usuários sempre podem criar um novo plano no planejador caso não haja nenhum existente](../../../../assets/images/faq/tab-planner-config.png)

![SharePoint também permite que o usuário cole diretamente um link de SharePoint](../../../../assets/images/faq/tab-sp-config.png)

### <a name="9989-tabs-in-channel---member-access"></a>guias &#9989; no canal - Acesso aos membros

* Uma guia configurada por um membro em um escopo de canal deve ser acessível aos outros membros sem ter que buscar permissões do membro que configurou a guia.
* O aplicativo deve fornecer as opções de gerenciamento de permissões antecipadamente se a guia for para uso privado ou restrito ou exigir quaisquer permissões do membro que configurou a guia.

### <a name="9989-bots-must-always-be-responsive-and-fail-gracefully"></a>&#9989; Bots devem estar sempre responsivos e falhar graciosamente

Seu bot deve responder a qualquer comando e não sem saída ao usuário. Aqui estão algumas dicas para ajudar seu bot a responder inteligentemente aos usuários:

* **Use listas de comando**. Analisar a entrada do usuário ou prever a intenção do usuário é difícil. Em vez de permitir que os usuários adivinhem o que seu bot pode fazer, forneça uma lista de comandos que seu bot entende.

![lista de comando Flow](../../../../assets/images/faq/flow-bot.png)

* **Inclua um comando de ajuda**. É provável que os usuários digitem "Ajuda" quando estão perdidos ou quando o bot não responde como esperado. Inclua um comando de ajuda que descreve como o valor do seu aplicativo será experimentado juntamente com todos os comandos válidos.

![Flow ajudar a comandar](../../../../assets/images/faq/flow-help.png)

* **Inclua conteúdo de ajuda ou orientação quando seu bot estiver perdido**. Quando o seu bot não consegue entender a entrada do usuário, ele deve sugerir uma ação alternativa. Por exemplo, *"Sinto muito, não entendo. Digite "ajuda" para obter mais informações."* Não responda com uma mensagem de erro ou simplesmente, *"Eu não entendo".*

### <a name="9989-help-command-response"></a>&#9989; ajuda a resposta de comando

* O Comando de Ajuda deve ser preciso e as respostas do aplicativo devem estar em um formato de cartão adaptativo com um conteúdo acionável para pelo menos seis comandos.
* Se um aplicativo tiver menos de seis comandos, verifique se todos os comandos estão presentes na placa adaptativa.

  ![Teste de comando de ajuda](../../../../assets/images/faq/helpcommand.png)

* **Use cartões adaptativos e módulos de tarefa para tornar a resposta do seu bot clara e acionável** 
 [Cartões adaptativos com botões invocando módulos de tarefas](/task-modules-and-cards/task-modules/task-modules-bots.md) melhoram a experiência do usuário do bot. Essas cartas e botões são mais fáceis de usar em um dispositivo móvel em vez de seu usuário digitar os comandos. Além disso, as respostas do bot não devem ser textuais com texto longo. Os bots devem fazer uso de cartões adaptativos e módulos de tarefa em vez de interface de usuário baseada em chat conversacional e longas respostas de texto.

* **Pense em todos os escopos.** Certifique-se de que seu bot fornece respostas apropriadas quando mencionado ( `@*botname*` ) em um canal e em conversas pessoais. Se o seu bot não fornecer um contexto significativo dentro do escopo pessoal ou das equipes, desabilitar esse escopo através do manifesto. (Veja o `bots` bloco na referência Microsoft Teams manifesto [esquema](../../../../resources/schema/manifest-schema.md#bots).)

* **Inclua equipe, bate-papo em grupo ou conversa 1:1**. As notificações de bot devem incluir uma equipe, um bate-papo em grupo ou uma conversa um-a-um com conteúdo relevante para o seu público.

* **Não pressione dados confidenciais**. Os bots não devem empurrar dados confidenciais para uma equipe, um bate-papo em grupo ou uma conversa de 1:1, onde há um público que não deve visualizar esses dados.

* **Forneça uma mensagem de boas-vindas.** O Bot deve fornecer uma mensagem de boas-vindas da FRE que inclui um tutorial interativo com cartões de carrossel ou botões de "experimentá-lo", para incentivar o engajamento.

### <a name="9989-personal-bots-must-always-send-a-welcome-message-on-first-launch"></a>&#9989; Bots pessoais devem sempre enviar uma mensagem de boas-vindas no primeiro lançamento

Uma mensagem de boas-vindas é a melhor maneira de definir o tom para o seu bot de bate-papo pessoal. Esta é a primeira interação que um usuário tem com o bot. Uma boa mensagem de boas-vindas pode encorajar o usuário a continuar explorando o aplicativo. Se a mensagem bem-vinda ou introdutória for confusa ou incerta, os usuários não verão o valor do aplicativo imediatamente e perderão o interesse.
Consulte a seção a seguir para obter requisitos de mensagem de boas-vindas:

> [!Note]
> Uma mensagem de boas-vindas é opcional para um bot de canal.

### <a name="welcome-message-requirements"></a>Requisitos de mensagem de boas-vindas

* Inclua uma proposta de valor com o tour de boas-vindas.
* Forneça orientações de encaminhamento para o uso do aplicativo.
* Inclua orientações sobre como se inscrever e configure seu aplicativo.
* Apresentar texto fácil de ler e diálogo direto — de preferência um cartão com um botão de visita de boas-vindas acionável que carrega um módulo de tarefa.
* Mantenha-o simples e utilizável com botões e cartões — evite textos longos, diálogos tagarelas.
* Inclua cartões e botões adaptativos para tornar a mensagem de boas-vindas mais utilizável.
* Invoque a mensagem de boas-vindas com um ping, não dois ou mais pings simultâneos.
* Uma mensagem de boas-vindas só deve ser mostrada ao usuário que configurou o aplicativo, de preferência em um chat pessoal 1:1.
* Os aplicativos pessoais devem sempre fornecer uma mensagem de boas-vindas a um usuário.
* Nunca envie uma conversa pessoal para cada membro da equipe; é considerado spam.
* Nunca envie a mensagem de boas-vindas mais de uma vez. Repetir a mesma mensagem de boas-vindas em intervalos regulares não é permitido e é considerado spam.

#### <a name="avoid-welcome-message-spamming"></a>Evite mensagens de boas-vindas spam

* **Mensagem de canal por bot**. Não faça spam de usuários criando novas postagens separadas. Crie uma única postagem de thread com respostas no mesmo segmento.
* **Bate-papo pessoal por bot**. Não envie várias mensagens. Envie uma mensagem com informações completas. Repetir a mesma mensagem de boas-vindas em intervalos regulares não é permitido e é considerado spam.

#### <a name="notification-only-bot-welcome-messages"></a>Mensagens de boas-vindas de bot somente para notificação

Os bots somente de notificação devem enviar uma mensagem de boas-vindas que inclua uma mensagem que *transmita: "Sou um bot somente de notificação e não serei capaz de responder aos seus chats"*.

#### <a name="welcome-messages-in-the-personal-scope"></a>Mensagens de boas-vindas no escopo pessoal

   * **Torne sua mensagem concisa e informativa.** A experiência do usuário e o conhecimento do seu aplicativo variam. Um usuário pode ter usado seu aplicativo em outra plataforma ou não saber nada sobre o seu aplicativo. Você quer adaptar sua mensagem a todos os públicos e em algumas frases explicar o que seu bot faz e as maneiras de interagir com ele. Você também deve explicar o valor do aplicativo e como os usuários se beneficiarão de usá-lo.
![Robô café e dinning](../../../../assets/images/faq/cafe-bot.png)

* **Torne sua mensagem acionável.** Pense na primeira coisa que você quer que os usuários façam depois de instalar seu aplicativo. Há algum comando legal que eles devem tentar? Há outra experiência de onboarding que eles devem saber? Eles precisam fazer login? Você pode adicionar ações em um cartão adaptativo ou fornecer exemplos específicos como *"Tente perguntar...."*, *"É isso que eu posso fazer..."*.

#### <a name="welcome-messages-in-the-team-or-channel--scope"></a>Mensagens de boas-vindas na equipe ou escopo do canal

As coisas são um pouco diferentes quando o bot é adicionado pela primeira vez a um canal. Normalmente, você não deve enviar uma mensagem 1:1 para todos da equipe, mas o bot pode enviar uma mensagem de boas-vindas no canal.

### <a name="9989-mobile-responsiveness-no-direct-upsell-or-payment"></a>&#9989; capacidade de resposta móvel, sem upsell direto ou pagamento

* Suas guias, cartões adaptativos, mensagens de bot e conteúdo em módulos de tarefa devem ser responsivos para uma variedade de tamanhos de telas de dispositivos móveis.
* Os aplicativos que suportam o iOS devem estar totalmente funcionais no mais recente dispositivo iPad usando a versão mais recente do iOS.
* Não deve incluir referências diretas a compras no aplicativo, ofertas de teste, ofertas para versões pagas ou links para quaisquer lojas online onde os usuários possam comprar ou adquirir outros conteúdos, aplicativos ou complementos do seu aplicativo Teams no sistema operacional móvel (Android, iOS).
* A versão iOS ou Android do complemento não deve mostrar qualquer interface do usuário ou idioma ou link para quaisquer outros aplicativos, complementos ou site que peçam ao usuário para pagar.
* As páginas da Política de Privacidade e dos Termos de Uso associadas também devem estar livres de qualquer usuário de comércio ou links da Loja.

### <a name="9989-do-not-post-sensitive-data-to-an-audience-not-intended-to-view-the-data"></a>&#9989; Não publique dados confidenciais para um público que não tenha a intenção de visualizar os dados

Seu aplicativo Teams não deve postar dados confidenciais, como cartão de crédito ou instrumento de pagamento financeiro, Informações Pessoais Identificáveis (PIN), saúde ou informações de rastreamento de contato para um público que não pretende visualizar esses dados.

### <a name="9989-do-not-transmit-financial-payment-details-or-complete-financial-transactions-via-your-teams-app"></a>&#9989; Não transmita detalhes de pagamentos financeiros ou complete transações financeiras através do seu aplicativo de Teams

* Seu aplicativo Teams não deve pedir aos usuários que façam um pagamento diretamente dentro Teams interface.
* Os aplicativos não podem transmitir detalhes do instrumento financeiro através do usuário na interface do aplicativo. Os aplicativos só podem transmitir links para proteger serviços de pagamento aos usuários se isso for divulgado nos Termos de Uso, Política de Privacidade e qualquer página de perfil ou site do aplicativo antes que um usuário concorde em usar o aplicativo.

### <a name="9989-clear-warning-before-downloading-any-files-or-executable-exe-into-a-users-environment"></a>&#9989; Aviso claro antes de baixar quaisquer arquivos ou executáveis ( `.exe` ) no ambiente de um usuário

Por favor, avise os usuários antes que seu aplicativo baixe quaisquer arquivos ou executáveis ( `.exe`  )na máquina ou ambiente do usuário.

### <a name="9989-messaging-extensions-must-provide-help-text-and-be-easy-to-read"></a>&#9989; As extensões de mensagens devem fornecer texto de ajuda e ser fáceis de ler

* A extensão de mensagens baseada em pesquisa deve fornecer texto de ajuda sobre como pesquisar efetivamente (por exemplo, mostrar entrada de exemplo).
* Os módulos de tarefa devem incluir um ícone e um nome curto em que estão contidos ou criados a partir do aplicativo.
* Os executáveis de extensão `@mention` de mensagem devem ser claros, fáceis de entender e fáceis de ler.
![Extensão de mensagem](../../../../assets/images/faq/message-extension.png)

## <a name="m365-publisher-attestation"></a>Atestado de Publisher M365

### <a name="9989-complete-the-publisher-attestation-in-partner-center"></a>&#9989; completar o atestado de Publisher em Centro de Parceiros

* Consulte a documentação completa do programa [Publisher Atestado](/microsoft-365-app-certification/docs/attestation) para obter mais detalhes.
* Siga os passos da seção [Publisher Atestado de Trabalho](/microsoft-365-app-certification/docs/userguide#3publisher-attestation-workflow) para concluir o processo de atestado do editor. Escreva para appcert@microsoft.com para qualquer dúvida.
* Consulte o [guia solução de problemas](/azure/active-directory/develop/troubleshoot-publisher-verification) para obter informações adicionais.
* Complete o auto-atestado através do centro de parceiros. Preencha o questionário de Self-Assessment em **Conformidade com aplicativos**.

## <a name="see-also"></a>Confira também

* [Saiba mais sobre Teams políticas de aprovação de aplicativos](/legal/marketplace/certification-policies#1140-teams)
* [Seção 100 — Geral](/legal/marketplace/certification-policies#100-general)
* [Seção 1100.5 — Controle do cliente](/legal/marketplace/certification-policies#11005-customer-control)
