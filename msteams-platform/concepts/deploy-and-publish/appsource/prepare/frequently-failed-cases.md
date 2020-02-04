---
title: Dicas e casos com falhas freqüentes
description: Descreve as dicas para o envio e a maioria das políticas com falha
keywords: perguntas frequentes de publicação do Microsoft Teams com frequência dicas de dica
ms.openlocfilehash: ffb472c918a205bdcf921b967269a80fcaa93338
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672790"
---
# <a name="tips-and-frequently-failed-cases"></a>Dicas e casos com falhas freqüentes 

Este artigo aborda alguns dos motivos mais comuns para os quais os aplicativos falham a validação. Ele não se destina a ser uma lista exaustiva de todos os possíveis problemas com seu aplicativo. No entanto, se você seguir essa orientação, a probabilidade de uma passagem pela primeira vez será bastante aumentada. Consulte a extensa lista de políticas aqui: [AppSource Validation Policies](https://dev.office.com/officestore/docs/validation-policies). As políticas na seção 14 das políticas de validação gerais do AppSource são específicas para os aplicativos do Microsoft Teams.

## <a name="tips-for-successful-app-submission"></a>Dicas para o envio bem-sucedido de aplicativos

* Verifique se você está usando a versão 1.4.1 ou posterior do SDK do Microsoft Teams.
* Não faça alterações em seu aplicativo enquanto a validação estiver em andamento. Isso exigirá uma revalidação completa do seu aplicativo.
* Seu aplicativo não deve parar de responder, terminar inesperadamente ou conter erros de programação. Se houver um problema, ele deverá falhar normalmente com uma mensagem de encaminhamento de maneira válida para o usuário.
* Seu aplicativo não deve baixar automaticamente, instalar ou iniciar qualquer código executável no ambiente do usuário. Qualquer download deve buscar uma permissão explícita do usuário.
* Qualquer material que você associar à sua experiência, como descrições e documentação de suporte, deve ser preciso. Use a verificação ortográfica, a capitalização, a pontuação e a gramática corretas em suas descrições e materiais.
* Ajuda e suporte: é altamente recomendável ter um link de ajuda/perguntas frequentes para seu aplicativo do Microsoft Teams e fornecer esse link na experiência de usuário de primeira execução. Para todos os aplicativos pessoais, recomendamos que você forneça a página de ajuda como uma guia pessoal para uma melhor experiência do usuário.

## <a name="policy-112-sign-up-sign-in-and-sign-out"></a>Política 11,2: inscrever-se, entrar e sair

Descrição: os aplicativos devem fornecer uma experiência clara, simples de entrada/saída e (quando apropriado). A experiência deve ser alcançável entre todos os recursos do aplicativo.

* Se houver uma opção de entrada explícita fornecida para o usuário, deverá haver uma opção de saída também (mesmo que o aplicativo esteja usando SSO/autenticação silenciosa)
* A opção de saída deve autenticar o usuário apenas da capacidade de seu aplicativo, e não do cliente do teams.
* Todos os escopos com uma entrada também devem ter uma assinatura. No mínimo, a opção de saída deve desconectar o usuário dos mesmos recursos nos quais a opção de entrada o assinou. Por exemplo, se a opção de entrada assinar o usuário em uma extensão de mensagens e uma guia, a opção de saída deverá desconectar o usuário da extensão da mensagem e da guia.

* Certifique-se de que haja sempre uma maneira de reverter os seguintes comportamentos (ou semelhantes):
  * Entrada => saída
  * Vincular uma conta/serviço => desvincular uma conta/serviço
  * Conectar uma conta/serviço => desconectar a conta/serviço
  * Autorizar uma conta/serviço => de/não autorizar a conta/serviço
  * Registrar uma conta/serviço => cancelar o registro da conta/serviço
* Se seu aplicativo requer uma conta ou serviço, você deve fornecer uma maneira para o usuário se inscrever ou solicitar a inscrição. Uma exceção pode ser procurada em um processo de inscrição se seu aplicativo se ajusta à categoria de aplicativo "corporativo".
* A funcionalidade de entrada/saída deve funcionar em clientes móveis. Verifique se você atualizou o SDK do seu Teams JavaScript para a versão 1.4.1 ou posterior.

Para obter informações adicionais sobre autenticação, consulte:

* [Documentação de autenticação](~/concepts/authentication/authentication.md)
* [Exemplo de autenticação de bot no nó](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
* [Exemplo de autenticação de guia no nó](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Autenticação de guia/bot no/.NET C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="policy-145-microsoft-teams-apps-must-respond-in-a-reasonable-timeframe"></a>Política 14,5: os aplicativos do Microsoft Teams devem responder em um prazo razoável.

* 14.5.1: para guias, se uma resposta a uma ação levar mais de três segundos, você deverá fornecer um aviso ou mensagem de carregamento.
* 14.5.2: para bots, uma resposta a um comando de usuário deve ocorrer dentro de dois segundos. Se for necessário processamento maior, você deverá usar um indicador de digitação.
* 14.5.3: para extensões de composição, uma resposta a um comando de usuário deve ocorrer dentro de cinco segundos.

> [!TIP]
> Certifique-se de incluir o indicador de carregamento quando o aplicativo estiver demorando muito.

## <a name="policy-14153-content-in-a-tab-should-not-have-superfluousunnecessary-ui-aka-ui-chrome-or-layered-navigation"></a>Política de 14.15.3: o conteúdo em uma guia não deve ter IU supérflua/desnecessária (aka: cromo da interface do usuário) ou navegação em camadas

As guias devem fornecer conteúdo focalizado e evitar elementos de interface do usuário que não estejam relacionados a esse conteúdo. Em geral, isso geralmente refere-se à navegação desnecessária/em camadas, não relacionada ou irrelevante ao lado do conteúdo ou qualquer link que leve o usuário ao conteúdo não relacionado ao conteúdo da guia. Por exemplo, o SharePoint removeu os menus de navegação e só tem o conteúdo principal na guia.

![Exibição da guia](~/assets/images/faq/web-sp.png)
![SharePoint do modo de exibição do SharePoint](~/assets/images/faq/tab-sp.png)

Se houver várias opções de exibição, considere ter um menu de configuração de tabulação para o usuário escolher. Por exemplo, em vez de incorporar um menu dentro da guia, as ideias amplas colocam o menu na página de configuração para que o modo de exibição de tabulação real seja limpo e focado.

![Página de configuração de grande ideia](~/assets/images/faq/wideidea.png)

## <a name="policy-14157-bots-must-respond-to-any-command-and-must-not-dead-end-the-user"></a>Política de 14.15.7: os bots devem responder a qualquer comando e não devem ficar inativo o usuário

Seu bot deve sempre ser responsivo. Aqui estão algumas dicas para ajudar seu bot a responder de forma mais inteligente aos usuários.

**Use a lista de comandos:** A análise de entrada do usuário ou a Predict intenções é difícil. Em vez de permitir que o usuário adivinhe o que o seu bot pode fazer, forneça aos usuários uma lista de comandos que seu bot possa entender.

![Lista de comandos de fluxo](~/assets/images/faq/flow-bot.png)

**Incluir um comando de ajuda:** É mais provável que os usuários digitem "ajuda" quando forem perdidos ou quando o bot não responder com o que estão esperando. Inclua um comando help que forneça sua proposta de valor junto com todos os seus comandos válidos.

![Comando Flow Help](~/assets/images/faq/flow-help.png)

**Inclua o conteúdo da ajuda ou orientações quando o bot for perdido:** Quando você não consegue entender a entrada do usuário, forneça um usuário com algo que poderíamos fazer em vez disso. Por exemplo, "Eu não entendo. Digite "ajuda" para obter mais informações. " Não responda com uma mensagem de erro ou simplesmente "Eu não compreendo". Use essa oportunidade para ensinar seus usuários.

**Considere o escopo:** Certifique-se de que seu bot forneça respostas apropriadas quando for mencionado (@*botname*) em um canal e em conversas pessoais, conforme necessário. Se o seu bot não fornecer um contexto significativo dentro do escopo pessoal ou do Teams, desabilite esse escopo por meio do manifesto. (Consulte o `bots` bloco na [referência do esquema de manifesto do Microsoft Teams](~/resources/schema/manifest-schema.md#bots).)

## <a name="policy-14159-bot-must-send-welcome-messages-on-the-first-launch"></a>Política de 14.15.9: o bot deve enviar mensagens de boas-vindas na primeira inicialização

As mensagens de boas-vindas são a melhor maneira de definir o Tom. Este é o primeiro usuário de interação com o bot. Uma boa mensagem de boas-vindas pode encorajar o usuário a continuar a explorar o aplicativo enquanto um inválido confundir o uso, e os usuários poderão perder os interesses se não conseguirem ver o valor do aplicativo imediatamente.

### <a name="personal-scope"></a>Escopo pessoal

Na primeira inicialização do bot, o usuário deve receber uma mensagem de boas-vindas do bot, mesmo antes de entrar. Algumas dicas para pensar ao criar sua mensagem de boas-vindas:

**Torne a mensagem concisa e informativa:** Os usuários podem ter experiências e conhecimento muito diferentes sobre seu aplicativo. Eles podem ter usado o aplicativo em outra plataforma ou não podem saber nada sobre seu aplicativo. Você deseja adaptar sua mensagem a todos os participantes e em algumas frases explique o que o seu bot faz e maneiras de interagir com ele. Você também deve explicar o valor do aplicativo e como os usuários se beneficiarão de usá-lo.
![Bot e bot dinning](~/assets/images/faq/cafe-bot.png)

**Tornar sua mensagem acionável:** Considere o que você deseja que os usuários façam após instalar seu aplicativo. Há algum comando interessante que deve tentar? Há outra experiência de integração que precisa saber? Eles precisam entrar? Você pode adicionar ações em um cartão adaptável ou fornecer exemplos específicos, como "Experimente fazer isso....", "é isso que eu posso fazer...".

### <a name="team-scope"></a>Escopo da equipe

As coisas são um pouco diferentes quando o bot é adicionado pela primeira vez a um canal. Normalmente, você não deve enviar uma mensagem 1:1 para todas as pessoas da equipe, mas o bot pode enviar uma mensagem de boas-vindas no canal.

## <a name="policy-141510-tab-configuration-ui-should-not-dead-end-the-experience-and-always-provide-a-way-for-a-user-to-continue"></a>Política de 14.15.10: a interface do usuário de configuração de guia não deve interromper a experiência e sempre fornecer uma maneira de o usuário continuar

Um usuário deve sempre ser capaz de concluir a experiência de configuração, mesmo que não possa encontrar imediatamente o conteúdo que está procurando. A experiência de configuração deve fornecer opções para o usuário localizar o conteúdo ou fixar uma URL ou criar um novo conteúdo se ele não existir. O usuário não deve ter que sair da experiência de configuração para criar conteúdo e voltar para o Microsoft Teams.

![O OneNote permite que os usuários colem um link do OneNote em não é possível encontrar anotações](~/assets/images/faq/tab-onenote-config.png)

![Os usuários sempre podem criar um novo plano no Planner, caso não haja nenhum existente](~/assets/images/faq/tab-planner-config.png)

![O SharePoint também permite que o usuário Cole diretamente um link do SharePoint](~/assets/images/faq/tab-sp-config.png)