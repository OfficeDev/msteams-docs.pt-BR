---
title: Dicas e casos com falhas freqüentes
description: Descreve as dicas para o envio e a maioria das políticas com falha
author: laujan
ms.author: lajanuar
ms.topic: how to
ms.openlocfilehash: 12d0f39da24fc6850d74c9c78728b6a9b6de587a
ms.sourcegitcommit: 576a4768b835422545cb6b6b3f75dce8318ea02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42896517"
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

![Exibição da guia](~/assets/images/faq/web-sp.png)
![SharePoint do modo de exibição do SharePoint](~/assets/images/faq/tab-sp.png)

* Se houver várias opções de exibição, considere ter um menu de configuração de tabulação para o usuário escolher. Por exemplo, em vez de incorporar um menu dentro da guia, coloque o menu na página de configuração para que o modo de exibição de tabulação real seja limpo e focado.

![Página de configuração de grande ideia](~/assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>A configuração da guia &#9989; deve acontecer na tela configuração

* A tela configuração deve explicar claramente o valor da experiência e como configurar a guia.
* O processo de configuração não deve ser encerrado, a experiência do usuário e sempre permite que os usuários continuem.
* Um usuário deve sempre ser capaz de concluir a experiência de configuração, mesmo que não possa encontrar imediatamente o conteúdo que está procurando.
* A experiência de configuração deve fornecer opções para que o usuário encontre o conteúdo, fixe uma URL ou crie um novo conteúdo se ele não existir.
* O usuário não deve ter que sair da experiência de configuração para criar conteúdo e voltar para o Microsoft Teams.

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

* **Considere todos os escopos**. Certifique-se de que o bot forneça respostas apropriadas quando`@*botname*`for mencionado () em um canal e em conversas pessoais. Se o seu bot não fornecer um contexto significativo dentro do escopo pessoal ou do Teams, desabilite esse escopo por meio do manifesto. (Consulte o `bots` bloco na [referência do esquema de manifesto do Microsoft Teams](~/resources/schema/manifest-schema.md#bots).)

### <a name="9989-bots-must-send-a-welcome-message-on-first-launch"></a>&#9989; bots devem enviar uma mensagem de boas-vindas na primeira inicialização

As mensagens de boas-vindas são a melhor maneira de definir o tom de seu bot. Esta é a primeira interação de um usuário com o bot. Uma boa mensagem de boas-vindas pode incentivar o usuário a continuar a explorar o aplicativo. Se a mensagem de boas-vindas ou introdutória for confusa ou innítida, os usuários não verão o valor do aplicativo imediatamente e perderão os interesses. A mensagem de boas-vindas deve incluir o seguinte:

* Um comando help.
* A proposta de valor
* Todos os comandos válidos.

Veja algumas considerações ao criar sua mensagem de boas-vindas:

#### <a name="personal-scope"></a>Escopo pessoal

* **Torne sua mensagem concisa e informativa**. Provavelmente, as experiências dos usuários e o conhecimento do seu aplicativo irão variar. Eles podem ter usado seu aplicativo em outra plataforma ou não sabem nada sobre seu aplicativo. Você deseja adaptar sua mensagem a todos os públicos e em algumas frases explique o que o seu bot faz e as maneiras de interagir com ele. Você também deve explicar o valor do aplicativo e como os usuários se beneficiarão de usá-lo.
![Bot e bot dinning](~/assets/images/faq/cafe-bot.png)

* **Tornar sua mensagem acionável**. Considere a primeira coisa que você deseja que os usuários façam após instalar seu aplicativo. Há um comando interessante que ele deve tentar? Há outra experiência de integração que precisa saber? Eles precisam entrar? Você pode adicionar ações em um cartão adaptável ou fornecer exemplos específicos, como *"Experimente fazer isso...."*, *"é isso que eu posso fazer..."*.

#### <a name="team-scope"></a>Escopo da equipe

As coisas são um pouco diferentes quando o bot é adicionado pela primeira vez a um canal. Normalmente, você não deve enviar uma mensagem 1:1 para todas as pessoas da equipe, mas o bot pode enviar uma mensagem de boas-vindas no canal.

> [!div class="nextstepaction"]
> [Saiba mais sobre as políticas de aprovação do teams app](/legal/marketplace/certification-policies#1140-teams) 
