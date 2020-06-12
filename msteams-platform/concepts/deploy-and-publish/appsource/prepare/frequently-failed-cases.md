---
title: Dicas e casos com falhas freqüentes
description: Descreve as dicas para o envio e a maioria das políticas com falha
author: laujan
ms.author: lajanuar
ms.topic: how to
ms.openlocfilehash: b2b198068478e6cc1e620d5bf5da9d448b3cf56d
ms.sourcegitcommit: b822584b643e003d12d2e9b5b02a0534b2d57d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2020
ms.locfileid: "44704478"
---
# <a name="tips-for-a-successful-app-submission"></a>Dicas para um envio de aplicativo bem-sucedido

Este artigo aborda razões comuns de falha na validação dos aplicativos enviados. Embora não tenha sido projetada para ser uma lista abrangente de todos os problemas em potencial com seu aplicativo, este guia aumentará a probabilidade de que seu envio de aplicativo seja transmitido pela primeira vez. *Consulte* [políticas de certificação do Marketplace comercial](/legal/marketplace/certification-policies) para obter uma lista extensa de políticas de validação.

>[!NOTE]
>A **[seção 1140](/legal/marketplace/certification-policies#1140-teams)** é específica para o Microsoft Teams e a **[subseção 1140,4](https://docs.microsoft.com/legal/marketplace/certification-policies#11404-functionality)** trata dos requisitos de funcionalidade para aplicativos do teams.

## <a name="validation-guidelines"></a>Diretrizes de validação

### <a name="9989-general-considerations"></a>&#9989; considerações gerais

*Consulte também* a [seção 100 — General](/legal/marketplace/certification-policies#100-general)

* Verifique se você está usando a versão 1.4.1 ou posterior do [SDK do Microsoft Teams](https://www.npmjs.com/package/@microsoft/teams-js).
* Não faça alterações em seu aplicativo enquanto o processo de validação estiver em andamento. Isso exigirá uma revalidação completa do seu aplicativo.
* Seu aplicativo não deve parar de responder, terminar inesperadamente ou conter erros de programação. Se for encontrado um problema, seu aplicativo deverá falhar normalmente e fornecer uma mensagem de encaminhamento à frente para o usuário.
* Seu aplicativo não deve baixar, instalar ou iniciar automaticamente qualquer código executável no ambiente do usuário. Todos os downloads devem buscar permissões explícitas do usuário.
* Qualquer material que você associar à sua experiência, como descrições e documentação de suporte, deve ser preciso. Use a verificação ortográfica, a capitalização, a pontuação e a gramática corretas em suas descrições e materiais.
* Fornecer informações de ajuda e suporte. É altamente recomendável que seu aplicativo inclua um link de ajuda/perguntas frequentes para a experiência do usuário de primeira execução. Para todos os aplicativos pessoais, recomendamos fornecer a página de ajuda como uma guia pessoal para uma melhor experiência do usuário.
* Aumente o número de versão do aplicativo no manifesto se você fizer alterações de manifesto no seu envio.

### <a name="9989--provide-a-clear-and-simple-sign-insign-out-and-sign-up-experience"></a>&#9989; fornecer uma experiência clara e simples de entrada/saída e inscrição

Seção *Consulte também* [1100,5 — controle de cliente](/legal/marketplace/certification-policies#11005-customer-control)

* Se seu aplicativo ou suplemento depender de contas ou serviços externos, a experiência de entrada/saída e inscrição deverá ser aparente e alcançável em todos os recursos do seu aplicativo.
* Se houver uma opção de entrada explícita fornecida para o usuário, deverá haver uma opção de saída correspondente (mesmo que o aplicativo esteja usando autenticação de SSO/[silenciosa](~/tabs/how-to/authentication/auth-silent-aad.md)).
* A opção de saída deve apenas desconectar o usuário da capacidade do seu aplicativo e não do cliente do teams.
* No mínimo, a opção de saída deve desconectar o usuário dos mesmos recursos acessados com a opção de entrada. Por exemplo, se a opção de entrada incluir uma extensão de mensagens e uma guia, a opção de saída deve incluir a extensão de mensagens e a guia.

* Certifique-se de que haja sempre uma maneira de reverter os seguintes comportamentos (ou semelhantes):
  * Entrar => sair.
  * Vincular uma conta/serviço => desvincular uma conta/serviço.
  * Conectar uma conta/serviço => desconectar uma conta/serviço.
  * Autorizar uma conta/serviço => desautorizar/negar uma conta/serviço.
  * Registrar uma conta/serviço => cancelar o registro/cancelar a assinatura de uma conta/serviço.
* Se seu aplicativo requer uma conta ou serviço, você deve fornecer uma maneira de o usuário se inscrever ou criar uma solicitação de inscrição. Uma exceção poderá ser concedida se o aplicativo for um aplicativo empresarial.
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

### <a name="9989-tab-content-should-not-have-excessive-chrome-or-layered-navigation"></a>O conteúdo da guia &#9989; não deve ter uma navegação em camadas ou cromo excessivo

* As guias devem fornecer conteúdo focalizado e evitar elementos de interface do usuário desnecessários. Em geral, isso geralmente se refere à navegação desnecessária/aninhada em camadas, uma interface do usuário estranha ou irrelevante ao lado do conteúdo ou qualquer link que leva o usuário a conteúdo não relacionado. Por exemplo, abaixo está um modo de exibição de guia que omite menus de navegação e apenas exibe o conteúdo principal:

![Modo de exibição da Web do SharePoint](~/assets/images/faq/web-sp.png)  
![Exibição da guia do SharePoint](~/assets/images/faq/tab-sp.png)

* As guias devem ter natureza clara e não incluir a navegação complexa.
* Se houver várias opções de exibição, considere ter um menu de configuração de tabulação para o usuário escolher. Por exemplo, em vez de incorporar um menu dentro da guia, coloque o menu na página de configuração para que o modo de exibição de tabulação real seja limpo e focado.

![Página de configuração de grande ideia](~/assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>A configuração da guia &#9989; deve acontecer na tela configuração

* A tela configuração deve explicar claramente o valor da experiência e como configurar a guia.
* O processo de configuração sempre deve fornecer uma maneira para que os usuários continuem não se desativam da experiência do usuário. Por exemplo, não mostre uma placa vazia após o usuário ter configurado a guia
* O processo de entrada do usuário deve fazer parte do processo de configuração e deve ser concluído na interface do usuário da guia. Depois que o usuário tiver concluído a configuração e carregado sua guia, nenhuma ação adicional deverá ser necessária.
* Não mostrar toda a sua página da Web na janela pop-up configuração de entrada.
* Um usuário deve sempre ser capaz de concluir a experiência de configuração, mesmo que não possa encontrar imediatamente o conteúdo que está procurando.
* A experiência de configuração deve fornecer opções para que o usuário encontre o conteúdo, fixe uma URL ou crie um novo conteúdo se ele não existir.
* A experiência de configuração deve permanecer no contexto do Microsoft Teams. O usuário não deve ter que sair da experiência de configuração para criar conteúdo e, em seguida, retornar ao Teams para fixá-lo.
* Use a área de visor disponível de forma eficiente. Não desperdice o uso de logotipos grandes dentro da configuração pop up

![O OneNote permite que os usuários colem um link do OneNote em não é possível encontrar anotações](~/assets/images/faq/tab-onenote-config.png)

![Os usuários sempre podem criar um novo plano no Planner, caso não haja nenhum existente](~/assets/images/faq/tab-planner-config.png)

![O SharePoint também permite que o usuário Cole diretamente um link do SharePoint](~/assets/images/faq/tab-sp-config.png)

### <a name="9989-bots-must-always-be-responsive-and-fail-gracefully"></a>Os bots de &#9989; devem sempre ser responsivos e falhar normalmente

O bot deve ser responsivo para qualquer comando e não para o usuário. Aqui estão algumas dicas para ajudar seu bot a responder de forma inteligente aos usuários:

* **Usar listas de comandos**. Analisar a entrada do usuário ou prever a intenção do usuário é difícil. Em vez de permitir que os usuários adivinhem o que o seu bot pode fazer, forneça uma lista de comandos que seu bot entenda.

![Lista de comandos de fluxo](~/assets/images/faq/flow-bot.png)

* **Incluir um comando help**. É provável que os usuários digitem "ajuda" quando forem perdidos ou quando o bot não responder conforme o esperado. Inclua um comando help que descreva como o valor do aplicativo será experiente em todos os comandos válidos.

![Comando Flow Help](~/assets/images/faq/flow-help.png)

* **Inclua o conteúdo da ajuda ou orientações quando seu bot for perdido**. Quando o bot não entende a entrada do usuário, ele deve sugerir uma ação alternativa. Por exemplo, *"Eu não entendo. Digite "ajuda" para obter mais informações. "* Não responda com uma mensagem de erro ou simplesmente, *"não compreendo"*. Use essa oportunidade para ensinar seus usuários.

* **Use cartões adaptáveis e módulos de tarefas para tornar sua resposta de bot clara e acionável** 
 [Cartões adaptáveis com botões que chamam módulos de tarefa](/task-modules-and-cards/task-modules/task-modules-bots) aprimoram a experiência do usuário do bot. Esses cartões e botões são mais fáceis de usar em um dispositivo móvel, em oposição ao usuário que está digitando os comandos

* **Considere todos os escopos**. Certifique-se de que o bot forneça respostas apropriadas quando for mencionado ( `@*botname*` ) em um canal e em conversas pessoais. Se o seu bot não fornecer um contexto significativo dentro do escopo pessoal ou do Teams, desabilite esse escopo por meio do manifesto. (Consulte o `bots` bloco na [referência do esquema de manifesto do Microsoft Teams](~/resources/schema/manifest-schema.md#bots).)

### <a name="9989-bots-must-send-a-welcome-message-on-first-launch"></a>&#9989; bots devem enviar uma mensagem de boas-vindas na primeira inicialização

As mensagens de boas-vindas são a melhor maneira de definir o tom de seu bot. Esta é a primeira interação de um usuário com o bot. Uma boa mensagem de boas-vindas pode incentivar o usuário a continuar a explorar o aplicativo. Se a mensagem de boas-vindas ou introdutória for confusa ou innítida, os usuários não verão o valor do aplicativo imediatamente e perderão os interesses.

### <a name="welcome-message-requirements"></a>Requisitos de mensagem de boas-vindas

* Identificar quem adicionou o bot a um canal.
* Incluir uma proposta de valor.
* Fornecer orientações para o uso do bot.
* Apresente o texto fácil de ler e uma caixa de diálogo direta — preferivelmente um cartão com um botão de Tour de boas-vindas acionável que carrega um módulo de tarefa.
* Mantenha-o simples, evite a caixa de diálogo de palavras/informativas.
* Invocar a mensagem de boas-vindas com um ping, não dois ou mais pings simultâneos.
* No bate-papo pessoal, a mensagem de boas-vindas só deve ser exibida para o usuário que configurou o aplicativo.  
* Nunca envie um chat pessoal para todos os membros da equipe.
* Nunca envie a mensagem de boas-vindas mais de uma vez. Repetir a mesma mensagem de boas-vindas por intervalos regulares não é permitida e é considerada como spam.

#### <a name="avoid-welcome-message-spamming"></a>Evitar o spam de mensagens de boas-vindas

* **Mensagem do canal por bot**. Não enviar spam a usuários criando novas postagens de chat separadas. Crie uma única postagem de thread com respostas no mesmo thread.
* **Chat pessoal por bot**. Não envie várias mensagens. Envie uma mensagem com informações completas.

#### <a name="notification-only-bot-welcome-messages"></a>Mensagens de boas-vindas do bot somente de notificação

Notificações apenas bots devem enviar uma mensagem de boas-vindas que inclui uma mensagem que se comunica, *"Eu sou um bot somente para notificação e não conseguirá responder a seus chat"*.

#### <a name="welcome-messages-in-the-personal-scope"></a>Mensagens de boas-vindas no escopo pessoal

* **Torne sua mensagem concisa e informativa**.  Provavelmente, a experiência do usuário com o e o conhecimento do seu aplicativo irão variar. Um usuário pode ter usado seu aplicativo em outra plataforma ou não sabe nada sobre seu aplicativo. Você deseja adaptar sua mensagem a todos os públicos e em algumas frases explique o que o seu bot faz e as maneiras de interagir com ele. Você também deve explicar o valor do aplicativo e como os usuários se beneficiarão de usá-lo.
![Bot e bot dinning](~/assets/images/faq/cafe-bot.png)

* **Tornar sua mensagem acionável**. Considere a primeira coisa que você deseja que os usuários façam após instalar seu aplicativo. Há um comando interessante que ele deve tentar? Há outra experiência de integração que precisa saber? Eles precisam entrar? Você pode adicionar ações em um cartão adaptável ou fornecer exemplos específicos, como *"Experimente fazer isso...."*, *"é isso que eu posso fazer..."*.

#### <a name="welcome-messages-in-the-teamchannel--scope"></a>Mensagens de boas-vindas no escopo de equipe/canal

As coisas são um pouco diferentes quando o bot é adicionado pela primeira vez a um canal. Normalmente, você não deve enviar uma mensagem 1:1 para todas as pessoas da equipe, mas o bot pode enviar uma mensagem de boas-vindas no canal.

> [!div class="nextstepaction"]
> [Saiba mais sobre as políticas de aprovação do teams app](/legal/marketplace/certification-policies#1140-teams) 
