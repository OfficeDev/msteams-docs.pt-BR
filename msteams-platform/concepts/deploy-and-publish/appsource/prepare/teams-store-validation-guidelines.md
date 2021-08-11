---
title: Microsoft Teams diretrizes de validação do armazenamento
description: Descreve as diretrizes que todos os aplicativos enviados ao Teams (AppSource) devem seguir.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 818fe6c9123e6a43788c650542b9e0aed6aeed90e0c78c72ae08f4d4f53d060a
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57703604"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Microsoft Teams diretrizes de validação do armazenamento

Seguir essas diretrizes aumenta a probabilidade de seu aplicativo passar no processo de envio Microsoft Teams de armazenamento. Essas Teams específicas da Microsoft complementam as políticas de certificação do [marketplace](/legal/marketplace/certification-policies) comercial da Microsoft e são atualizadas com frequência para refletir novos recursos, comentários do usuário e alterações nas regras de negócios.

> [!NOTE]
> Algumas diretrizes podem não ser aplicáveis ao seu aplicativo. Por exemplo, se seu aplicativo não incluir um bot, você poderá ignorar as diretrizes relacionadas ao bot.

## <a name="value-proposition"></a>Proposta de valor

### <a name="app-name"></a>Nome do aplicativo

O nome de um aplicativo desempenha uma função crítica na forma como os usuários o descobrem na loja. Lembre-se do seguinte sobre nomes de aplicativo:

* O nome deve incluir termos relevantes para seus usuários.
* Nomes de recursos Teams principais&#8212;como **Chat,** **Contatos,** **Calendário,** **Chamadas,** **Arquivos,** Atividade, **Teams,** **Aplicativos** e Ajuda **&#8212;** não devem ser **incluídos** no nome do aplicativo.
* Os substantivos comuns devem ser prefixados ou sufixos com o nome do desenvolvedor (por exemplo, **Contoso Tasks** em vez de **Tarefas**).
* Não deve usar **Teams** ou outros nomes de produtos da Microsoft que podem indicar falsamente a co-identidade visual ou a co-venda. (Para obter mais informações sobre como fazer referência a softwares, produtos e serviços da Microsoft, consulte As Diretrizes de Marca e [Marca da Microsoft).](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)
* Se seu aplicativo faz parte de uma parceria oficial com a Microsoft, o nome do seu aplicativo deve vir primeiro (por exemplo, **Conector contoso para** Microsoft Teams ).
* Não é necessário copiar o nome de um aplicativo listado na loja ou outra oferta no marketplace comercial.
* Não deve conter termos profano ou depreciativo. O nome também não deve incluir linguagem racial ou culturalmente insensível.
* Deve ser exclusivo. Por exemplo, você não pode listar vários aplicativos para regiões diferentes com o mesmo nome e funcionalidade.

### <a name="suitable-for-workplace-consumption"></a>Adequado para consumo no local de trabalho

O conteúdo do aplicativo deve ser adequado para o consumo geral do local de trabalho e respeitar todas as restrições listadas nas políticas de certificação do marketplace comercial. O conteúdo relacionado à política, à política, ao jogo e ao entretenimento prolongado é proibido. Para obter mais informações, consulte as políticas [de certificação do marketplace comercial.](/legal/marketplace/certification-policies#10010-inappropriate-content)

Seu aplicativo deve facilitar a colaboração em grupo, melhorar a produtividade de um indivíduo ou ambos. Os aplicativos destinados à união de equipe e à socialização devem ser colaborativos e projetados para vários participantes. Esses tipos de aplicativos também não devem exigir um investimento de tempo substancial ou afetar perceptivamente a produtividade.

### <a name="similar-platforms-and-services"></a>Plataformas e serviços semelhantes

Os aplicativos devem se concentrar na experiência Teams e não incluir os nomes, ícones ou imagens de outras plataformas ou serviços semelhantes de colaboração baseadas em chat, a menos que seu aplicativo fornece interoperabilidade específica.

### <a name="feature-names"></a>Nomes de recursos

Os nomes de recursos do aplicativo em botões e outros textos da interface do usuário não devem entrar em conflito com a terminologia reservada para Teams e outros produtos Microsoft. Por exemplo, **Iniciar reunião,** **Fazer chamada** ou **Iniciar chat**. Inclua seu nome de aplicativo se você não puder evitar completamente isso, como Iniciar reunião **da Contoso** em vez de **Iniciar reunião**.

## <a name="security"></a>Segurança

### <a name="microsoft-365-app-compliance-program"></a>Programa de Conformidade de Aplicativos do Microsoft 365

O [Microsoft 365 de Conformidade](/microsoft-365-app-certification/overview) de Aplicativos destina-se a ajudar as organizações a avaliar e gerenciar riscos avaliando informações de segurança e conformidade sobre seu aplicativo. Se você estiver publicando um aplicativo na Teams, deverá concluir as seguintes camadas do programa:

* [Publisher Verificação](/azure/active-directory/develop/publisher-verification-overview): ajuda os administradores e usuários finais a entender a autenticidade dos desenvolvedores de aplicativos que se integram ao plataforma de identidade da Microsoft. Quando concluído, um selo "verificado" azul é exibido na caixa de diálogo de consentimento Azure Active Directory (Azure AD) e em outras telas. Para obter mais informações, [consulte perguntas frequentes](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), como marcar seu aplicativo como [editor verificado](/azure/active-directory/develop/mark-app-as-publisher-verified)e solucionar problemas de verificação [do editor.](/azure/active-directory/develop/troubleshoot-publisher-verification)
* [Publisher Atestado](/microsoft-365-app-certification/docs/attestation): um processo no qual você compartilha informações gerais, de tratamento de dados e de segurança e conformidade para ajudar os clientes em potencial a tomar decisões informadas sobre como usar seu aplicativo.

> [!NOTE]
> Se você estiver enviando um aplicativo que não tenha sido listado anteriormente, não poderá concluir oficialmente Publisher Atestado até que seu aplicativo esteja no Teams store. Se você estiver atualizando um aplicativo listado, conclua Publisher Atestado antes de enviar a versão mais recente do aplicativo.

### <a name="bots"></a>Bots

Para aplicativos que usam o serviço Microsoft Azure Bot (como bots e extensões de mensagens), você deve seguir todos os requisitos definidos nos Termos do Microsoft [Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46).

Os bots sempre devem pedir permissão para carregar um arquivo e exibir uma mensagem de confirmação após o carregamento do arquivo.

### <a name="external-domains"></a>Domínios externos

Na maioria dos casos, você não deve incluir domínios fora do controle da sua organização (incluindo curingas) e serviços de túnel nas configurações de domínio do seu aplicativo. As seguintes exceções incluem:

* Se seu aplicativo usar o OAuthCard do Serviço de Bot do Azure, você deverá incluir como um domínio válido ou o botão Entrar `token.botframework.com` não funcionará. 
* Se seu aplicativo se baseia em SharePoint, você pode incluir o site raiz associado SharePoint como um domínio válido usando a `{teamSiteDomain}` propriedade context.

### <a name="authentication"></a>Autenticação

Para obter informações sobre como implementar a autenticação de aplicativos, consulte [authentication in Teams](~/concepts/authentication/authentication.md).

#### <a name="authenticating-with-external-services"></a>Autenticação com serviços externos

Lembre-se do seguinte se seu aplicativo autentica usuários com um serviço externo.

* **Entre, saia e inscreva-se experiências**:
  * Os aplicativos que dependem de contas ou serviços externos devem fornecer experiências claras e simples de entrar, sair e inscrever-se.
  * Quando um usuário sai, ele deve sair apenas do aplicativo e permanecer Teams.
* Experiências **de compartilhamento** de conteúdo : os aplicativos que exigem autenticação com um serviço externo para compartilhar conteúdo em canais Teams devem apresentar claramente na documentação de ajuda (ou recursos semelhantes) como desconectar ou desconectar conteúdo se esse recurso tiver suporte no serviço externo. Isso não significa que a capacidade de desahar o conteúdo deve estar presente em seu Teams app.

#### <a name="government-community-cloud-listings"></a>Nuvem da Comunidade Governamental listagem

Para distribuir seu aplicativo para usuários Nuvem da Comunidade Governamental (GCC) enquanto evita listagens duplicadas no armazenamento Teams, o processo de autenticação deve identificar e encaminhar os usuários para uma URL específica ou esperada do GCC.

### <a name="sensitive-content"></a>Conteúdo sensível

Seu aplicativo não deve postar dados confidenciais, como cartão de crédito ou dados de instrumento de pagamento financeiro. O aplicativo também não deve exibir a saúde, o rastreamento de contatos ou outras informações de identificação pessoal (PII) para uma audiência que não se destina a exibir esse conteúdo.

Avisar os usuários antes que seu aplicativo baixe arquivos ou executáveis (.exe) no computador ou ambiente do usuário.

### <a name="financial-information"></a>Informações financeiras

Os aplicativos não devem solicitar que os usuários façam pagamentos na Teams interface. Os detalhes do instrumento financeiro não devem ser transmitidos aos usuários por meio de uma interface bot.

Você só poderá vincular a serviços de pagamento externos e seguros se tiver feito a divulgação apropriada em seus termos de uso, política de privacidade ou qualquer página de perfil ou site antes de o usuário concordar em usar o aplicativo.

Os aplicativos em execução na versão para iOS ou Android do Teams devem seguir as seguintes diretrizes:

* Os aplicativos não devem incluir compras no aplicativo, ofertas de avaliação ou interface do usuário que visam a atualização para versões pagas ou links para lojas online onde os usuários podem comprar ou adquirir outros conteúdos, aplicativos ou complementos.
* Se seu aplicativo exigir uma conta, os usuários devem ser capazes de se inscrever em uma conta sem custo. O uso do termo **conta gratuita** ou **gratuita** é proibido.
* Você pode determinar se uma conta está ativa indefinidamente ou por um tempo limitado, mas se a conta expirar, nenhuma interface do usuário, texto ou links indicando a necessidade de pagamento pode ser mostrado.
* A política de privacidade e os termos de uso do seu aplicativo devem estar livres de qualquer interface do usuário ou links relacionados ao comércio.

## <a name="general-functionality-and-performance"></a>Funcionalidade geral e desempenho

### <a name="launching-external-functionality"></a>Iniciar funcionalidade externa

Os aplicativos não devem tirar os usuários Teams cenários principais do usuário. O conteúdo e as interações do aplicativo podem ocorrer Teams recursos, como bots, cartões e módulos de tarefa.

Você deve vincular usuários em algum lugar Teams e não a um site ou aplicativo externo. Para cenários que exigem funcionalidade externa, seu aplicativo deve ter permissão explícita do usuário para iniciar essa funcionalidade.

### <a name="compatibility"></a>Compatibilidade

Os aplicativos devem estar totalmente funcionais nos seguintes sistemas operacionais e navegadores:

* Microsoft Windows 7 e posterior
* macOS 10.10 e posterior
* Microsoft Edge 12 e posterior
* Mozilla Firefox 47.0 e posterior
* Google Chrome 51.0 e posterior
* iOS 9.0 e posterior
* Android 4.4 e posterior

### <a name="response-time"></a>Hora da resposta

Teams aplicativos devem responder dentro de um prazo razoável, que varia dependendo da funcionalidade.

* As guias devem responder dentro de três segundos ou exibir uma mensagem de carregamento ou aviso.
* Os bots devem responder aos comandos do usuário em dois segundos ou exibir um indicador de digitação.
* As extensões de mensagens devem responder aos comandos do usuário em cinco segundos.
* As notificações devem ser exibidas dentro de cinco segundos após a ação do usuário.

## <a name="app-package-and-store-listing"></a>Listagem do pacote de aplicativos e da loja

Os pacotes de aplicativos devem ser formatados corretamente e incluir todas as informações e componentes necessários.

### <a name="app-manifest"></a>Manifesto do aplicativo

O Teams de aplicativo define as configurações do aplicativo.

* Seu manifesto deve estar em conformidade com o esquema de manifesto mais recente. Para obter informações, consulte a [referência de manifesto](~/resources/schema/manifest-schema.md).
* Se seu aplicativo incluir um bot ou uma extensão de mensagens, seu manifesto deve ser consistente com metadados da Estrutura de Bot, incluindo nome de bot, logotipo, link de política de privacidade e termos de link de serviço.
* Se seu aplicativo usa Azure Active Directory (Azure AD) para autenticação, inclua a ID do Aplicativo do Azure AD (cliente) no manifesto. Para obter mais informações, consulte a [referência do manifesto](~/resources/schema/manifest-schema.md#webapplicationinfo).

### <a name="app-icons"></a>Ícones de aplicativo

Os ícones são um dos principais elementos que as pessoas veem ao navegar no Teams store. Seus ícones devem comunicar a marca e a finalidade do aplicativo, ao mesmo tempo que aderem aos seguintes requisitos:

* Seu pacote de aplicativos deve incluir duas versões PNG do ícone do aplicativo: um ícone de cor e um ícone de contorno.
* A versão colorida do ícone é exibida na maioria Teams cenários e deve ter 192 x 192 pixels. Seu símbolo de ícone (96 x 96 pixels) pode ser qualquer cor ou cores, mas deve estar em um plano de fundo quadrado sólido ou totalmente transparente.
* A versão de contorno do ícone é exibida quando seu aplicativo está em uso e "içada" na barra de aplicativos no lado esquerdo do Teams e quando um usuário fixa a extensão de mensagens do aplicativo. Ele deve ter 32 x 32 pixels e pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco (nenhuma outra cor é permitida). O ícone não deve ter nenhum preenchimento extra ao redor do símbolo.
* Ícones formatados e dimensionados corretamente devem ser incluídos no pacote do aplicativo. Os ícones também devem corresponder ao que é enviado com os metadados de listagem da loja.

Para obter mais informações, práticas recomendadas e exemplos, consulte as diretrizes Teams [ícones do](~/concepts/build-and-test/apps-package.md#app-icons)aplicativo.

### <a name="app-descriptions"></a>Descrições do aplicativo

Você deve ter uma descrição curta e longa do seu aplicativo. As descrições nas configurações do aplicativo e no Partner Center devem ser as mesmas.

As descrições não devem ser diretamente ou por meio da insinuação menosprezem outra marca (propriedade da Microsoft ou de outra forma). Certifique-se de que sua descrição não inclua declarações que não podem ser fundamentadas (por exemplo, "Aumento garantido de 200% na eficiência").

#### <a name="short-description"></a>Descrição breve

Uma breve descrição é um resumo conciso do seu aplicativo que realça sua proposta de valor e é direcionado para seu público-alvo.

**Faça:**

* Mantenha a descrição curta em uma frase.
* Fale primeiro as informações mais importantes.
* Inclua palavras-chave que os clientes provavelmente procurarão.

**Não faça:**

* Repita o nome do aplicativo.
* Use o aplicativo **word** na descrição curta.

#### <a name="long-description"></a>Descrição longa

A descrição longa pode fornecer uma narração envolvente que realça a proposta de valor do aplicativo, o público principal e o setor de destino. Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.

**Faça:**

* Use [Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) para formatar sua descrição.
* Use voz ativa e fale diretamente com os usuários. Por exemplo, *Você pode ...*.
* List features with bullet points so it's easier to scan the description.
* Descreva claramente limitações, condições ou exceções para a funcionalidade, recursos e produtos de entrega descritos na listagem e materiais relacionados antes que o usuário instale seu aplicativo. Os Teams recursos que seu aplicativo oferece suporte devem estar relacionados às funções principais que sua listagem descreve.
* Inclua uma ajuda ou um link de suporte.
* Consulte **Microsoft 365** em vez de **Office 365**.
* Se você precisar fazer referência **Teams,** escreva a primeira referência como **Microsoft Teams**. Referências subsequentes podem ser reduzidas **para Teams**.
* Use o seguinte idioma ao descrever como o aplicativo funciona com Teams (ou Microsoft 365):
  * "... funciona com Microsoft Teams."
  * "... trabalhando com Microsoft Teams."
  * "... dentro Microsoft Teams."
  * "... para Microsoft Teams."

**Não faça:**

* Exceder 500 palavras.
* Abreviar **a Microsoft** como **MS** ou **MSFT**.
* Indique que o aplicativo é uma oferta da Microsoft, incluindo o uso de lemas ou linhas de marcação da Microsoft.
* Use nomes de marca protegidos por direitos autorais que você não possui.
* Inclua erros de digitação, erros gramaticais e maiúsculas desnecessárias (por exemplo, **Usuários** em vez de **usuários**).
* Inclua links para AppSource.
* Use o seguinte idioma, a menos que você seja um parceiro certificado da Microsoft:
  * "... integrado ao Microsoft Teams"
  * "... integra-se com ..."
  * "... built for ..."
  * "... built on ..."
  * "... é executado em ..."
  * "... habilitado por ..."
  * "... certificado para ..."
  * "... desenvolvido para ..."
  * "... projetado para ..."

### <a name="screenshots"></a>Capturas de tela

As capturas de tela fornecem uma visualização visual proeminente do seu aplicativo para complementar o nome, o ícone e as descrições do aplicativo. Lembre-se do seguinte sobre capturas de tela:

* Você pode ter até cinco capturas de tela por listagem.
* Os tipos de arquivo com suporte incluem PNG, JPEG e GIF.
* As dimensões devem ter 1366 x 768 pixels.
* Tamanho máximo de 1.024 KB.

**Faça:**

* Concentre-se nos recursos do seu aplicativo (por exemplo, como as pessoas podem se comunicar com seu bot).
* Inclua conteúdo que represente com precisão seu aplicativo.
* Use texto criteriosamente.
* Capturas de tela de quadro com uma cor que reflete sua marca e incluem conteúdo de marketing, semelhante ao exemplo de listagem [do Freshdesk](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) (requisitos de dimensão se aplicam à imagem inteira e não apenas à captura de tela).

**Não faça:**

* Mostrar dispositivos específicos, como telefones ou laptops.
* Exibe o cromado ou a interface do usuário que não está em seu aplicativo.
* Capture qualquer Teams ou interface do usuário do navegador em suas capturas de tela.
* Inclua mockups que reflitam imprecisamente a interface do usuário real do aplicativo, como mostrar seu aplicativo sendo usado fora do Teams.

> [!TIP]
> Um vídeo pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Um vídeo também é a primeira coisa que os usuários veem em sua listagem (por padrão, um vídeo é exibido antes das capturas de tela). Para obter mais informações, [consulte create a video for your store listing](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

### <a name="privacy-policy"></a>Política de privacidade

A política de privacidade pode ser específica para seu aplicativo Teams ou uma política geral para todos os seus serviços.

* Se você usar um modelo de política de privacidade genérico, deverá fazer referência a **serviços,** aplicativos e **plataformas** para incluir seu aplicativo Teams seu serviço ou site.
* Deve incluir como você lida com armazenamento, retenção e exclusão de dados do usuário. Você também deve descrever os controles de segurança que você usa para proteção de dados.
* Deve incluir suas informações de contato.
* Não deve conter URLs que estão quebradas ou para fins beta ou de preparação.
* Não deve incluir links para AppSource.

### <a name="terms-of-use"></a>Termos de uso

Seus termos de uso devem ser específicos e aplicáveis à sua oferta.

### <a name="support-links"></a>Links de suporte

As URLs de suporte do aplicativo não devem exigir autenticação. Por exemplo, os usuários não devem ter que fazer logoff para entrar em contato com você.

### <a name="localization"></a>Localização

Se seu aplicativo oferece suporte à localização, seu pacote de aplicativos deve incluir um arquivo com traduções de idioma que são exibidas com base na configuração Teams idioma. O arquivo deve estar em conformidade com o Teams de localização. Para obter mais informações, consulte o [Teams de localização](~/concepts/build-and-test/apps-localization.md).

## <a name="tabs"></a>Guias

Se seu aplicativo incluir uma guia, certifique-se de que ele adere a essas diretrizes.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte Teams diretrizes de [design de guia.](~/tabs/design/tabs.md)

### <a name="setup"></a>Configurar

* A configuração de tabulação não deve encerrar um novo usuário. Forneça uma mensagem sobre como concluir a ação ou o fluxo de trabalho.
* A autenticação deve acontecer durante a configuração da guia e não depois.

### <a name="views"></a>Modos de exibição

* A área de tela de login não deve usar logotipos grandes ou exibir uma página da Web inteira.
* O conteúdo pode ser simplificado quebrando-o entre várias guias.
* As guias não devem ter um header duplicado. Remova o logotipo do iframe já que a estrutura de tabulação já exibe o ícone e o nome do aplicativo.

### <a name="navigation"></a>Navegação

* As guias não devem ter mais de três níveis de navegação.
* As guias não devem fornecer navegação que conflita com a navegação Teams principal.
* As páginas secundárias e terciárias em uma guia devem ser abertas em uma exibição de nível dois e nível três na área de tabulação principal, que é navegada por meio de larguras ou navegação à esquerda. Você também pode incluir os seguintes componentes para ajudar a navegação de guia:
    * Botões voltar
    * Headers de página
    * Menus de hambúrguer
* A guia não deve ter rolagem horizontal.
* Links profundos em guias não devem se vincular a uma página da Web externa, mas em algum lugar dentro Teams. Por exemplo, módulos de tarefa ou outras guias.
* As guias não devem permitir que os usuários naveguem fora Teams para a experiência principal do aplicativo.

### <a name="usability"></a>Usabilidade

* As guias devem fornecer valor além de apenas hospedar um site existente.
* Os usuários devem ser capazes de desfazer sua última ação na guia.
* Guias em um contexto pessoal podem agregar conteúdo de instâncias compartilhadas do aplicativo.
* As guias devem ser responsivas Teams temas. Quando um usuário altera o tema, o tema do aplicativo deve refletir a seleção.
* As guias devem usar Teams com estilo de Teams, como fontes de Teams, rampas de tipo, paletas de cores, sistema de grade, movimento, tom de voz e assim por diante sempre que possível.
* Você deve incluir uma **guia Configurações.**
* As guias devem seguir Teams design de interação, como, navegação na página, posição e uso de caixas de diálogo, hierarquias de informações e assim por diante sempre que possível.
* O conteúdo de tabulação no iframe não deve incluir recursos que imitam Teams principais recursos. Por exemplo, bots, extensões de mensagens, chamada, reunião e assim por diante.

> [!TIP]
>
> * Inclua um bot pessoal junto com uma guia pessoal.
> * Permitir que os usuários compartilhem conteúdo de sua guia pessoal.

## <a name="bots"></a>Bots

Se seu aplicativo incluir um bot, certifique-se de que ele adere a essas diretrizes.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes Teams de design de bot.](~/bots/design/bots.md)

### <a name="bot-commands"></a>Comandos bot

Analisar a entrada do usuário e prever a intenção do usuário é difícil. Os comandos bot fornecem aos usuários um conjunto de palavras ou frases que seu bot entende para que eles (e seu bot) não tenham que adivinhar.

* A listagem de comandos bot com suporte nas configurações do aplicativo é altamente recomendada. Esses comandos são exibidos na caixa de redação quando um usuário tenta enviar uma mensagem ao bot.
* Todos os comandos compatíveis com o bot devem funcionar corretamente, incluindo o **comando Hi**, **Hello** e **Help.**

> [!TIP]
> Para bots pessoais, inclua uma **guia Ajuda** que descreve ainda mais o que seu bot pode fazer.

### <a name="bot-welcome-messages"></a>Mensagens de boas-vindas de bot

* Os bots quase sempre devem enviar uma mensagem de boas-vindas durante a primeira executar. Para a melhor experiência, a mensagem deve incluir a proposta de valor do bot, como configurar o bot e descrever brevemente todos os comandos de bot com suporte. Você pode exibir a mensagem usando um Cartão Adaptável com botões para melhor usabilidade. Para obter mais informações, consulte como disparar uma mensagem de [boas-vindas do bot.](~/bots/how-to/conversations/send-proactive-messages.md)
* As mensagens de boas-vindas do bot em canais e chats são opcionais durante a primeira execução, especialmente se o bot estiver disponível para uso pessoal e executar ações semelhantes. Se o bot enviar mensagens de boas-vindas, ele não deverá enviá-los para os usuários individualmente (isso é considerado [spam](#bot-message-spamming)). A mensagem também deve mencionar a pessoa que adicionou o bot.
* Os bots somente notificação devem enviar uma mensagem de boas-vindas que transmite que ela não responderá às mensagens dos usuários.

> [!TIP]
> Em mensagens de boas-vindas a usuários individuais, um tour de carrossel pode fornecer uma visão geral eficaz do bot e de todos os outros recursos do aplicativo. Incluindo botões, os comandos de bot permitem que os usuários experimentem são incentivados. Por exemplo, **Criar uma tarefa**.

### <a name="bot-message-spamming"></a>Spam de mensagens bot

Os bots não devem spam de usuários enviando várias mensagens em breve.

* **Mensagens bot em canais e chats**: Não spam usuários criando postagens separadas. Crie uma única postagem com respostas no mesmo thread.
* **Mensagens bot em aplicativos pessoais**: Não envie várias mensagens em sucessão rápida. Envie uma mensagem com informações completas. Evite conversas multi-turn para concluir um único fluxo de trabalho. Em vez disso, considere usar um formulário (ou módulo de tarefa) para coletar todas as entradas de um usuário de uma só vez.
* **Mensagens de boas-vindas**: Repetir a mesma mensagem de boas-vindas em intervalos regulares não é permitido e considerado spam. Por exemplo, quando um novo membro é adicionado a uma equipe, não spam os outros membros com uma mensagem de boas-vindas. Em vez disso, mensagem ao novo membro pessoalmente.

### <a name="bot-notifications"></a>Notificações de bot

As notificações de bot devem incluir conteúdo relevante para o escopo definido para o bot (equipe, chat ou pessoal).

### <a name="bots-and-adaptive-cards"></a>Bots e Cartões Adaptáveis

Cartões adaptáveis são uma maneira altamente recomendada de exibir mensagens bot. Seus cartões devem ser leves e incluir apenas ações de 1 a 3. Se você precisar exibir mais conteúdo, considere usar um módulo de tarefa ou uma guia.

Para obter mais informações, consulte os seguintes recursos:

* [Criar Cartões Adaptáveis](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Referência de cartões](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

## <a name="messaging-extensions"></a>Extensões de mensagens

Se seu aplicativo incluir uma extensão de mensagens, certifique-se de que ele adere a essas diretrizes.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as diretrizes Teams de design de [extensão de mensagens.](~/messaging-extensions/design/messaging-extension-design.md)

### <a name="action-commands"></a>Comandos de ação

As extensões de mensagens baseadas em ação devem fazer o seguinte:

* Permitir que os usuários acionem ações em uma mensagem sem concluir etapas intermediárias, como entrar.
* Passe o contexto da mensagem para o próximo estado de trabalho.

### <a name="preview-links-link-unfurling"></a>Links de visualização (link desfraldamento)

As extensões de mensagens devem visualizar links reconhecidos na caixa Teams de redação. Não adicione domínios que estão fora do seu controle (URLs absolutas ou curingas). Por exemplo, `yourapp.onmicrosoft.com` é válido, `*.onmicrosoft.com` mas não é válido. Domínios de nível superior também são proibidos (por exemplo, `*.com` ou `*.org` ).

### <a name="search-commands"></a>Comandos de pesquisa

* As extensões de mensagens baseadas em pesquisa devem fornecer texto que ajude os usuários a pesquisar efetivamente.
* @mention executáveis devem ser claros, fáceis de entender e acessível.

## <a name="task-modules"></a>Módulos de tarefas

Um módulo de tarefa deve incluir um ícone e o nome curto do aplicativo ao seu associado.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte Teams diretrizes de design do [módulo de tarefa.](~/task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="meeting-extensions"></a>Extensões de reunião

Se seu aplicativo incluir uma extensão de reunião, certifique-se de que ele adere a essas diretrizes.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as diretrizes Teams de design de [extensão de reunião.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)

### <a name="pre--and-post-meeting-experience"></a>Experiência pré e pós-reunião

* As telas pré e pós-reunião devem seguir as diretrizes gerais de design de guias. Para obter mais informações, consulte as [diretrizes Teams design.](~/tabs/design/tabs.md)
* As guias não devem ter rolagem horizontal.
* As guias devem ter um layout organizado ao exibir vários itens. Por exemplo, mais de 10 pesquisas ou pesquisas. Consulte um [exemplo de layout](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Seu aplicativo deve notificar os usuários quando os resultados de uma pesquisa ou sondagem são exportados informando: "Resultados baixados com êxito".

### <a name="in-meeting-experience"></a>Experiência na reunião

* Os aplicativos só devem usar um tema escuro durante as reuniões. Para obter mais informações, consulte as [diretrizes Teams design.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming)
* Uma dica de ferramenta deve exibir o nome do aplicativo ao passar o mouse sobre o ícone do aplicativo durante as reuniões.
* As extensões de mensagens devem funcionar da mesma forma durante as reuniões que fazem fora das reuniões.

### <a name="in-meeting-tabs"></a>Guias na reunião

* Deve ser responsivo. Certifique-se de manter tamanhos de preenchimento e componentes.
* Deve ter um botão voltar se houver mais de uma camada de navegação.
* Não deve incluir mais de um botão de demissão ou fechamento. Isso pode confundir os usuários, já que já há um botão de header integrado para descartar a guia.
* Não deve ter rolagem horizontal.

### <a name="in-meeting-dialogs"></a>Caixas de diálogo na reunião

* Deve ser usado com moderação e para cenários que são leves e orientados a tarefas.
* Deve exibir conteúdo em uma única coluna e não ter vários níveis de navegação.
* Não deve usar módulos de tarefa.
* Deve alinhar-se ao centro do estágio de reunião.
* Deve ser ignorado quando um usuário seleciona um botão ou executa uma ação.

## <a name="notifications"></a>Notificações

Se seu aplicativo usa as [APIs](/graph/teams-send-activityfeednotifications)de feed de atividade fornecidas pela Microsoft Graph , certifique-se de que ele adere às seguintes diretrizes.

### <a name="general"></a>Geral

* Todos os gatilhos de notificação especificados em suas configurações de aplicativo devem receber uma notificação no aplicativo.
* As notificações devem ser localizadas de acordo com os idiomas com suporte configurados para seu aplicativo.
* As notificações devem ser exibidas dentro de cinco segundos após a ação do usuário.

### <a name="avatars"></a>Avatares

* O avatar de notificação deve corresponder ao ícone de cor do aplicativo.
* As notificações disparadas por um usuário devem incluir o avatar do usuário.

### <a name="spamming"></a>Spam

* Os aplicativos não devem enviar mais de 10 notificações por minuto para um usuário.
* Os bots e o feed de atividade não devem disparar notificações duplicadas.
* As notificações devem fornecer algum valor aos usuários e não serem usadas para eventos triviais ou irrelevantes.

### <a name="navigation-and-layout"></a>Navegação e layout

* As notificações devem seguir o layout e a experiência do feed de Teams atividade.
* Ao selecionar uma notificação, o usuário deve ser direcionado para conteúdo relevante dentro Teams e não retirado da experiência Teams.

## <a name="advertising"></a>Publicidade

Os aplicativos não devem exibir publicidade, incluindo anúncios dinâmicos, anúncios em faixa e anúncios em mensagens.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma conta do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
