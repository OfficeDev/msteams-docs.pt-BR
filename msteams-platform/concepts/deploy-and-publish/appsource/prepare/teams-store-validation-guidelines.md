---
title: Diretrizes de validação da loja do Microsoft Teams
description: Descreve as diretrizes que todos os aplicativos enviados à loja do Teams (AppSource) devem seguir.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: 5e2f26fcdbd2e11fcb28331cd9d226d63c9a2aad
ms.sourcegitcommit: 762cd3ed9054c6c19825498fc0edd50cd99634da
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2021
ms.locfileid: "59439687"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Diretrizes de validação da loja do Microsoft Teams

Seguir essas diretrizes aumenta a probabilidade de que seu aplicativo seja aprovado no processo de envio da loja do Microsoft Teams. Essas diretrizes específicas do Teams complementam as [políticas de certificação do mercado comercial](/legal/marketplace/certification-policies) da Microsoft e são atualizadas com frequência para refletirem novos recursos, comentários do usuário e alterações de regras de negócios.

> [!NOTE]
> É possível que algumas diretrizes não sejam pertinentes ao seu aplicativo. Por exemplo, se seu aplicativo não incluir um bot, você poderá ignorar as diretrizes relacionadas ao bot.

## <a name="value-proposition"></a>Proposta de valor

### <a name="app-name"></a>Nome do aplicativo

O nome de um aplicativo desempenha um papel fundamental na forma como os usuários o descobrem na loja. Lembre-se do seguinte quanto aos nomes de aplicativo:

* O nome deve incluir termos relevantes aos seus usuários.
* Nomes dos principais recursos&#8212 do Teams;como **Bate-papo**, **Contatos**, **Calendário**, **Chamadas**, **Arquivos**, **Atividade**, **Teams**, **Aplicativos** e **Ajuda**&#8212;não devem ser incluídos no nome do aplicativo.
* Os substantivos comuns devem conter prefixo ou sufixo com o nome do desenvolvedor (por exemplo, **Tarefas da Contoso** em vez de **Tarefas**).
* Não se deve usar **Teams** ou outros nomes de produtos da Microsoft que possam indicar falsamente o uso de marcas ou vendas conjuntas. (Para obter mais informações sobre como fazer referência a softwares, produtos e serviços da Microsoft, consulte [Diretrizes de Marca e Marca da Microsoft](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)).
* Se seu aplicativo fizer parte de uma parceria oficial com a Microsoft, o nome do seu aplicativo deve vir primeiro (por exemplo, **Conector Contoso do Microsoft Teams**).
* Não é preciso copiar o nome de um aplicativo listado na loja ou em outra oferta no mercado comercial.
* Não deve conter termos profanos ou depreciativos. O nome também não deve incluir linguagem racial ou culturalmente insensível.
* Deve ser exclusivo. Por exemplo, você não pode listar vários aplicativos para regiões diferentes com o mesmo nome e funcionalidade.

### <a name="suitable-for-workplace-consumption"></a>Adequado para o consumo no local de trabalho

O conteúdo do aplicativo deve ser adequado ao consumo geral no local de trabalho e obedecer a todas as restrições listadas nas políticas de certificação do mercado comercial. É proibido o conteúdo relacionado à religião, política, jogos de azar e entretenimento prolongado. Para obter mais informações, consulte as [políticas de certificação do mercado comercial](/legal/marketplace/certification-policies#10010-inappropriate-content).

Seu aplicativo deve facilitar a colaboração em grupo, melhorar a produtividade de um indivíduo, ou ambos. Os aplicativos destinados à união e socialização da equipe devem ser colaborativos e projetados para vários participantes. Esses tipos de aplicativos também não devem exigir um investimento substancial de tempo ou causar um impacto perceptível na produtividade.

### <a name="similar-platforms-and-services"></a>Plataformas e serviços semelhantes

Os aplicativos devem se concentrar na experiência do Teams e não incluir nomes, ícones ou imagens de outras plataformas ou serviços de colaboração semelhantes baseados em bate-papo, a menos que seu aplicativo ofereça interoperabilidade específica.

### <a name="feature-names"></a>Nomes de recursos

Os nomes de recursos do aplicativo em botões e outros textos da IU não devem entrar em conflito com a terminologia reservada ao Teams e outros produtos da Microsoft. Por exemplo, **Iniciar reunião**, **Fazer chamadas** ou **Iniciar bate-papo**. Inclua o nome do seu aplicativo se você não puder evitar isso completamente, como **Iniciar reunião da Contoso** em vez de **Iniciar reunião**.

## <a name="security"></a>Segurança

### <a name="microsoft-365-app-compliance-program"></a>Programa de Conformidade do Aplicativo do Microsoft 365

O [Programa de Conformidade dos Aplicativos do Microsoft 365](/microsoft-365-app-certification/overview) tem como objetivo ajudar as organizações a avaliarem e gerenciarem riscos através da avaliação de informações de segurança e conformidade do seu aplicativo. Se você publicar um aplicativo na loja do Teams, precisará concluir os seguintes níveis do programa:

* [Verificação do Editor](/azure/active-directory/develop/publisher-verification-overview): ajuda os administradores e usuários finais a entenderem a autenticidade dos desenvolvedores de aplicativos que se integram à plataforma de identidade da Microsoft. Quando concluído, um selo "verificado" azul é exibido na caixa de diálogo de consentimento do Azure Active Directory (Azure AD). assim como em outras telas. Para obter mais informações, consulte [perguntas frequentes](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [como marcar seu aplicativo como publicador verificado](/azure/active-directory/develop/mark-app-as-publisher-verified)e [solução de problemas de verificação do editor](/azure/active-directory/develop/troubleshoot-publisher-verification).
* [Atestado do Editor](/microsoft-365-app-certification/docs/attestation): um processo no qual você compartilha informações gerais, de tratamento de dados, e de segurança e conformidade para ajudar os clientes em potencial a tomarem decisões informadas sobre como usar seu aplicativo.

> [!NOTE]
> Se você enviar um aplicativo que não tenha sido listado anteriormente, não poderá concluir oficialmente o Atestado do Editor até que seu aplicativo esteja na loja do Teams. Se você atualizar um aplicativo listado, conclua o Atestado do Editor antes de enviar a versão mais recente do aplicativo.

### <a name="bots"></a>Bots

Para aplicativos que usam o Serviço de Bot do Microsoft Azure (como bots e extensões de mensagens), você deve seguir todos os requisitos definidos nos Termos do Microsoft [Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46).

Os bots sempre devem pedir permissão para carregar um arquivo e exibir uma mensagem de confirmação depois de carregar o arquivo.

### <a name="external-domains"></a>Domínios externos

Na maioria dos casos, você não deve incluir domínios fora do controle da sua organização (incluindo curingas) e serviços de túnel nas configurações de domínio do seu aplicativo. As seguintes exceções incluem:

* Se seu aplicativo usar o OAuthCard do Serviço de Bot do Azure, você deverá incluir `token.botframework.com` como um domínio válido ou o botão **Entrar** não funcionará.
* Se seu aplicativo depender do SharePoint, você poderá incluir o site raiz associado do SharePoint como um domínio válido usando a `{teamSiteDomain}` propriedade do contexto.

### <a name="authentication"></a>Autenticação

Para obter informações sobre como implementar a autenticação do aplicativo, consulte [autenticação no Teams](~/concepts/authentication/authentication.md).

#### <a name="authenticating-with-external-services"></a>Autenticação com serviços externos

Lembre-se do seguinte se seu aplicativo autentica usuários com um serviço externo.

* **Entre, saia e inscreva-se em experiências**:
  * Os aplicativos que dependem de contas ou serviços externos devem fornecer experiências de entrada, saída e inscrição claras e simples.
  * Quando um usuário sai, ele deve sair apenas do aplicativo e permanecer no Teams.
* **Experiências de compartilhamento de conteúdo**: os aplicativos que exigem autenticação com um serviço externo para compartilhar o conteúdo nos canais do Teams devem indicar claramente na documentação de ajuda (ou recursos semelhantes) como desconectar ou descompartilhar o conteúdo se esse recurso tiver suporte no serviço externo. Isso não significa que a capacidade de descompartilhar o conteúdo deve estar presente no seu aplicativo do Teams.

#### <a name="government-community-cloud-listings"></a>Listas da Nuvem Comunitária Governamental

Para distribuir seu aplicativo aos usuários da Nuvem da Comunidade Governamental (GCC), ao mesmo tempo em que evita listas duplicadas na loja do Teams, o processo de autenticação deve identificar e encaminhar os usuários para uma URL específica ou esperada da GCC.

### <a name="sensitive-content"></a>Conteúdo confidencial

Seu aplicativo não deve postar dados confidenciais, como cartão de crédito ou dados de instrumento de pagamento financeiro. O aplicativo também não deve exibir a integridade, o rastreamento de contatos ou outras informações de identificação pessoal (PII) a um público que não quer exibir esse conteúdo.

Avise os usuários antes que seu aplicativo baixe arquivos ou executáveis (.exe) no computador ou ambiente do usuário.

### <a name="financial-information"></a>Informações financeiras

Os aplicativos não devem solicitar que os usuários façam pagamentos na interface do Teams. Os detalhes do instrumento financeiro não devem ser transmitidos aos usuários por uma interface de bot.

Você só poderá vincular a serviços de pagamento seguros e externos se tiver feito a divulgação apropriada nos seus termos de uso, política de privacidade ou páginas de perfil ou sites antes de o usuário concordar em usar o aplicativo.

Os aplicativos em execução na versão para iOS ou Android do Teams devem seguir as seguintes diretrizes:

* Os aplicativos não devem incluir compras no aplicativo, ofertas de avaliação ou IU que visam a venda adicional nas versões pagas ou links de lojas online em que os usuários podem comprar ou adquirir outros conteúdos, aplicativos ou suplementos.
* Se seu aplicativo exigir uma conta, os usuários devem conseguir se inscrever em uma conta sem custo. É proibido o uso do termo **gratuito** ou **conta gratuita**.
* Você pode determinar se uma conta estará ativa indefinidamente ou por um tempo limitado, mas se a conta expirar, nenhuma interface do usuário, texto ou links indicando a necessidade de pagamento poderá ser exibido.
* A política de privacidade e os termos de uso do seu aplicativo devem estar livres de IU ou links relacionados ao comércio.

## <a name="general-functionality-and-performance"></a>Funcionalidade e desempenho gerais

### <a name="launching-external-functionality"></a>Iniciar a funcionalidade externa

Os aplicativos não devem tirar os usuários do Teams de cenários de usuários centrais. O conteúdo e as interações do aplicativo podem ocorrer nos recursos do Teams, como bots, cartões e módulos de tarefas.

Você deve vincular os usuários em algum lugar do Teams e não a um site ou aplicativo externo. Quanto aos cenários que exigem funcionalidade externa, seu aplicativo deve ter permissão explícita do usuário para iniciar essa funcionalidade.

### <a name="compatibility"></a>Compatibilidade

Os aplicativos devem ser totalmente funcionais nos seguintes sistemas operacionais e navegadores:

* Microsoft Windows 7 e versão mais recente
* macOS 10.10 e versão mais recente
* Microsoft Edge 12 e versão mais recente
* Mozila Firefox 47.0 e versão mais recente
* Google Chrome 51.0 e versão mais recente
* iOS 9.0 e versão mais recente
* Android 4.4 e versão mais recente

### <a name="response-time"></a>Tempo de resposta

Os aplicativos do Teams devem responder dentro de um período razoável, o que varia dependendo da funcionalidade.

* As guias devem responder dentro de três segundos ou exibir uma mensagem ou aviso de carregamento.
* Os bots devem responder aos comandos do usuário dentro de dois segundos ou exibir um indicador de digitação.
* As extensões de mensagens devem responder aos comandos do usuário dentro de cinco segundos.
* As notificações devem ser exibidas dentro de cinco segundos a contar da ação do usuário.

## <a name="app-package-and-store-listing"></a>Lista do pacote de aplicativos e da loja.

Os pacotes de aplicativos devem ser formatados corretamente e incluir todas as informações e componentes necessários.

### <a name="app-manifest"></a>Manifesto do aplicativo

O manifesto do aplicativo do Teams define as configurações do aplicativo.

* Seu manifesto deve estar de acordo com o esquema de manifesto mais recente. Para obter mais informações, consulte a [referência do manifesto](~/resources/schema/manifest-schema.md).
* Se seu aplicativo incluir uma extensão bot ou de mensagens, seu manifesto deve ser consistente com os metadados do Estrutura do Bot, incluindo o nome do bot, logotipo, link da política de privacidade e link dos termos de serviço.
* Se seu aplicativo usar o Azure Active Directory (Azure AD) para autenticação, inclua a ID do aplicativo Azure AD (cliente) no manifesto. Para obter mais informações, consulte a [referência do manifesto](~/resources/schema/manifest-schema.md#webapplicationinfo).

### <a name="app-icons"></a>Ícones do aplicativo

Os ícones são um dos principais elementos que as pessoas visualizam ao navegar na loja do Teams. Seus ícones devem comunicar a marca e a finalidade do seu aplicativo e, ao mesmo tempo, cumprir com os seguintes requisitos:

* O pacote do seu aplicativo deve incluir duas versões PNG do ícone do seu aplicativo: um ícone de cor e um ícone de contorno.
* A versão colorida do seu ícone é exibida na maioria dos cenários do Teams e deve ter 192 x 192 pixels. O símbolo do seu ícone (96x96 pixels) pode ser de qualquer cor ou cores, mas deve ficar sobre um fundo quadrado sólido ou totalmente transparente.
* A versão de contorno do seu ícone exibe quando seu aplicativo está em uso e "içado" na barra de aplicativos no lado esquerdo do Teams e quando um usuário fixa a extensão de mensagens do seu aplicativo. Ele deve ter 32 x 32 pixels e pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco (não são permitidas outras cores). O ícone não deve ter preenchimentos extras ao redor do símbolo.
* Os ícones dimensionados e formatados corretamente devem ser incluídos no pacote do aplicativo. Os ícones também devem corresponder ao que é enviado com os metadados listados da loja.

Para obter mais informações, práticas recomendadas e exemplos, consulte as [diretrizes do ícone](~/concepts/build-and-test/apps-package.md#app-icons) do aplicativo do Teams.

### <a name="app-descriptions"></a>Descrições do aplicativo

Você deve ter uma descrição curta e longa do seu aplicativo. As descrições nas configurações do seu aplicativo e na Central de parceiros devem ser as mesmas.

As descrições não devem depreciar, diretamente ou por insinuação, outra marca (de propriedade da Microsoft ou de outra forma). Certifique-se de que sua descrição não inclua declarações que não possam ser fundamentadas (por exemplo, "Aumento garantido de 200% na eficiência").

#### <a name="short-description"></a>Descrição breve

Uma breve descrição é um resumo conciso do seu aplicativo que destaca sua proposta de valor e é dirigida ao seu público-alvo.

**Fazer:**

* Manter a descrição curta em uma frase.
* Colocar primeiro as informações mais importantes.
* Incluir palavras-chave que os clientes provavelmente procurarão.

**Não fazer:**

* Repetir o nome do aplicativo.
* Usar a palavra **aplicativo** na descrição curta.

#### <a name="long-description"></a>Descrição longa

A longa descrição pode fornecer uma narrativa envolvente que destaca a proposta de valor, o público principal e o setor-alvo do seu aplicativo. Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.

**Fazer:**

* Usar [Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) para formatar sua descrição.
* Usar a voz ativa e falar diretamente com os usuários. Por exemplo, *Você pode...*.
* Listar os recursos com marcadores para que seja mais fácil escanear a descrição.
* Descrever de forma clara as limitações, condições ou exceções da funcionalidade, recursos e produtos de entrega descritos na lista, assim como materiais relacionados antes de o usuário instalar seu aplicativo. Os recursos do Teams que seu aplicativo oferece suporte devem estar relacionados às funções principais que sua lista descreve.
* Inclua uma ajuda ou um link de suporte.
* Consulte **Microsoft 365** em vez de **Office 365**.
* Se você precisar referenciar o **Teams**, escreva a primeira referência como **Microsoft Teams**. As referências subsequentes podem ser reduzidas para **Teams**.
* Use a seguinte linguagem ao descrever como o aplicativo funciona com o Teams (ou com o Microsoft 365):
  * "... funciona com o Microsoft Teams."
  * "... trabalhando com o Microsoft Teams."
  * "... dentro do Microsoft Teams."
  * "... do Microsoft Teams."
  * "... integrado com o Microsoft Teams."
  * "... criado para... "
  * "... desenvolvido para... "
  * "... projetado para..."


**Não fazer:**

* Exceder 500 palavras.
* Abreviar **Microsoft** como **MS** ou **MSFT**.
* Indicar que o aplicativo é uma oferta da Microsoft, incluindo o uso de lemas ou linhas de marcação da Microsoft.
* Usar nomes de marca protegidos por direitos autorais que você não possui.
* Incluir erros de digitação, erros gramaticais e letras maiúsculas desnecessárias (por exemplo, **Usuários** em vez de **usuários**).
* Incluir links ao AppSource.
* Usar a seguinte linguagem, a menos que você seja um parceiro certificado da Microsoft:
  * "... certificado para ..."
  * "... alimentado por ..."

### <a name="screenshots"></a>Capturas de tela

As capturas de tela fornecem uma visualização panorâmica proeminente do seu aplicativo para complementar seu nome, ícone e descrições. Lembre-se do seguinte sobre capturas de tela:

* Você pode ter até cinco capturas de tela por lista.
* Os tipos de arquivo com suporte incluem PNG, JPEG e GIF.
* As dimensões devem ter 1366x768 pixels.
* Tamanho máximo de 1.024 KB.

**Fazer:**

* Concentrar-se nos recursos do seu aplicativo (por exemplo, como as pessoas podem se comunicar com seu bot).
* Incluir conteúdo que represente com precisão seu aplicativo.
* Usar texto de forma criteriosa.
* Capturas de tela de quadro com uma cor que reflita sua marca e incluem conteúdo de marketing, semelhante ao exemplo da [Lista do Freshdesk](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) (requisitos de dimensão se aplicam à imagem inteira e não apenas à captura de tela).

**Não fazer:**

* Mostrar dispositivos específicos, como telefones ou laptops.
* Exibir o Chrome ou a IU que não estiverem no seu aplicativo.
* Capture qualquer Teams ou IU do navegador nas suas capturas de tela.
* Incluir maquetes que reflitam de forma imprecisa a IU real do seu aplicativo, como por exemplo, mostrar seu aplicativo sendo usado fora do Teams.

> [!TIP]
> Um vídeo pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Um vídeo também é a primeira coisa que os usuários visualizam na sua lista (por padrão, um vídeo é exibido antes das capturas de tela). Para obter mais informações, consulte [criar um vídeo para a lista da sua loja](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

### <a name="privacy-policy"></a>Política de privacidade

A política de privacidade pode ser específica ao seu aplicativo do Teams ou uma política geral para todos os seus serviços.

* Se você usar um modelo de política de privacidade genérico, deverá referenciar **serviços**, **aplicativos** e **plataformas** para incluir seu aplicativo do Teams, assim como seu serviço ou site.
* Deve incluir como você lida com o armazenamento, retenção e exclusão de dados do usuário. Você também deve descrever os controles de segurança que você usa para proteger dados.
* Deve incluir suas informações de contato.
* Não deve conter URLs que estejam corrompidas ou para fins beta ou de teste.
* Não deve incluir links para AppSource.

### <a name="terms-of-use"></a>Termos de uso

Seus termos de uso devem ser específicos e aplicáveis à sua oferta.

### <a name="support-links"></a>Links de suporte

As URLs de suporte do aplicativo não devem exigir autenticação. Por exemplo, os usuários não devem ter que fazer login para entrarem em contato com você.

### <a name="localization"></a>Localização

Se o seu aplicativo oferece suporte à localização, o pacote do aplicativo deve incluir um arquivo com traduções de idiomas que são exibidos com base na configuração de idioma do Teams. O arquivo deve estar em conformidade com o esquema de Localização do Teams. Para obter mais informações, consulte a [Localização do Teams](~/concepts/build-and-test/apps-localization.md).

## <a name="tabs"></a>Guias

Se seu aplicativo incluir uma guia, certifique-se de que ele siga essas diretrizes.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [Diretrizes de design da guia do Teams](~/tabs/design/tabs.md).

### <a name="setup"></a>Configurar

* A configuração da guia não deve deixar um novo usuário sem saída. Forneça uma mensagem sobre como concluir a ação ou o fluxo de trabalho.
* A autenticação deve acontecer durante a configuração da guia e não depois.

### <a name="views"></a>Visualizações

* A área da tela de login não deve usar logotipos grandes ou exibir uma página da Web inteira.
* O conteúdo pode ser simplificado dividindo-o em várias guias.
* As guias não devem conter um cabeçalho duplicado. Remova o logotipo do iframe, pois a estrutura da guia já exibe o ícone e o nome do aplicativo.

### <a name="navigation"></a>Navegação

* As guias não devem conter mais de três níveis de navegação.
* As guias não devem fornecer navegação que entre em conflito com a navegação primária do Teams.
* As páginas secundárias e terciárias em uma guia devem ser abertas em uma visualização de nível dois e três na área da guia principal, que é navegada por trilhas ou navegação à esquerda. Você também pode incluir os seguintes componentes para ajudar a navegação de guia:
    * Botões de voltar
    * Cabeçalhos da página
    * Menus de hambúrguer
* A guia não deve possuir rolagem horizontal.
* Os links profundos nas guias não devem possuir um link em uma página da Web externa, mas em algum lugar dentro do Teams. Por exemplo, módulos de tarefas ou outras guias.
* As guias não devem permitir que os usuários naveguem fora do Teams em busca da experiência do aplicativo principal.

### <a name="usability"></a>Usabilidade

* As guias devem fornecer valor além de apenas hospedar um site existente.
* Os usuários devem poder desfazer sua última ação na guia.
* As guias em um contexto pessoal podem agregar conteúdo de instâncias compartilhadas do aplicativo.
* As guias devem responder aos temas do Teams. Quando um usuário altera o tema, o tema do aplicativo deve refletir a seleção.
* As guias devem usar componentes de estilo do Teams, como fontes do Teams, rampas de tipo, paletas de cores, sistema de grade, movimento, tom de voz, e assim por diante, sempre que possível.
* As guias devem seguir o design de interação do Teams, como navegação na página, posição e uso de caixas de diálogo, hierarquias de informações, e assim por diante, sempre que possível.
* O conteúdo da guia no iframe não deve incluir recursos que imitam os principais recursos do Teams. Por exemplo, bots, extensões de mensagens, chamada, reunião, e assim por diante.

> [!TIP]
>
> * Inclua um bot pessoal junto com uma guia pessoal.
> * Permitir que os usuários compartilhem o conteúdo da sua guia pessoal.

## <a name="bots"></a>Bots

Se seu aplicativo incluir um bot, certifique-se de que ele siga essas diretrizes.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [Diretrizes de design do bot do Teams](~/bots/design/bots.md).

### <a name="bot-commands"></a>Comandos do bot

Analisar a entrada do usuário e prever a intenção do usuário é difícil. Os comandos do bot fornecem aos usuários um conjunto de palavras ou frases que o seu bot entende para que eles (e o seu bot) não tenham que adivinhar.

* A lista de comandos de bot com suporte nas configurações do aplicativo é altamente recomendada. Esses comandos são exibidos na caixa de composição quando um usuário tenta enviar uma mensagem ao bot.
* Todos os comandos compatíveis com o bot devem funcionar corretamente, incluindo os comandos **Oi**, **Olá** e **Ajuda**.

> [!TIP]
> Quanto aos bots pessoais, inclua uma guia **Ajuda** que descreve ainda mais o que seu bot pode fazer.

### <a name="bot-welcome-messages"></a>Mensagens de boas-vindas do bot

* Os bots quase sempre devem enviar uma mensagem de boas-vindas durante a primeira execução. Para a melhor experiência, a mensagem deve incluir a proposta de valor do seu bot, como configurar o bot e descrever brevemente todos os comandos de bot com suporte. Você pode exibir a mensagem usando um Cartão Adaptável com botões para uma melhor usabilidade. Para obter mais informações, consulte [como acionar uma mensagem de boas-vindas do bot](~/bots/how-to/conversations/send-proactive-messages.md).
* As mensagens de boas-vindas do bot em canais e bate-papos são opcionais durante a primeira execução, especialmente se o bot estiver disponível para uso pessoal e executar ações semelhantes. Se o bot enviar mensagens de boas-vindas, ele não deverá enviá-los aos usuários individualmente (isso é considerado [spam](#bot-message-spamming)). A mensagem também deve mencionar a pessoa que adicionou o bot.
* Os bots somente para notificação devem enviar uma mensagem de boas-vindas que transmite que não responderá às mensagens dos usuários.

> [!TIP]
> Em mensagens de boas-vindas a usuários individuais, uma visita por carrossel pode fornecer uma visão geral eficaz do seu bot e de outras características do aplicativo. É recomendável incluir botões para permitir que os usuários experimentem comandos de bot. Por exemplo, **Criar uma tarefa**.

### <a name="bot-message-spamming"></a>Spam de mensagens de bot

Os bots não devem enviar spam aos usuários, enviando várias mensagens consecutivas.

* **Mensagens de bot em canais e bate-papos**: não enviar spam aos usuários criando postagens separadas. Crie uma única postagem com respostas na mesma conversa.
* **Mensagens de bot em aplicativos pessoais**: não envie várias mensagens consecutivas. Envie uma mensagem com informações completas. Evite conversas de várias voltas para completar um único fluxo de trabalho. Em vez disso, considere usar um formulário (ou módulo de tarefa) para coletar todas as entradas de um usuário de uma só vez.
* **Mensagens de boas-vindas**: repetir a mesma mensagem de boas-vindas em intervalos regulares não é permitido e considerado spam. Por exemplo, quando um novo membro é adicionado a uma equipe, não crie spam para outros membros com uma mensagem de boas-vindas. Em vez disso, envie uma mensagem ao novo membro pessoalmente.

### <a name="bot-notifications"></a>Notificações de bot

As notificações de bot devem incluir conteúdo relevante ao escopo definido pelo bot (equipe, bate-papo ou pessoal).

### <a name="bots-and-adaptive-cards"></a>Bots e Cartões Adaptáveis

Os Cartões Adaptáveis são uma forma altamente recomendada de exibir mensagens de bot. Seus cartões devem ser leves e incluir apenas 1 a 3 ações. Se for necessário exibir mais conteúdo, considere usar um módulo de tarefas ou uma guia.

Consulte os seguintes recursos para obter mais informações:

* [Design dos Cartões Adaptáveis](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Referência dos cartões](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

## <a name="messaging-extensions"></a>Extensão de mensagens

Se seu aplicativo incluir uma extensão de mensagens, certifique-se de que ele siga essas diretrizes.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [Diretrizes de design da extensão de mensagens do Teams](~/messaging-extensions/design/messaging-extension-design.md).

### <a name="action-commands"></a>Comandos de ação

As extensões de mensagens baseadas em ação devem realizar o seguinte:

* Permitir que os usuários acionem ações em uma mensagem sem concluir etapas intermediárias, como entrar.
* Transferir o contexto da mensagem ao próximo estado de trabalho.

### <a name="preview-links-link-unfurling"></a>Links de visualização (desenrolar do link)

As extensões de mensagens devem visualizar os links reconhecidos na caixa de composição do Teams. Não adicione domínios que estejam fora do seu controle (URLs absolutas ou curingas). Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido. Os domínios de primeiro nível também são proibidos (por exemplo, `*.com` ou `*.org` ).

### <a name="search-commands"></a>Comandos de pesquisa

* As extensões de mensagens baseadas em pesquisa devem fornecer textos que ajudem os usuários a pesquisarem com eficiência.
* @menções executáveis devem ser claras, fáceis de entender, e acessíveis.

## <a name="task-modules"></a>Módulos de tarefas

Um módulo de tarefa deve incluir um ícone e o nome curto do aplicativo ao qual está associado.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte [Diretrizes de design do módulo de tarefas do Teams](~/task-modules-and-cards/task-modules/design-teams-task-modules.md).

## <a name="meeting-extensions"></a>Extensões da reunião

Se seu aplicativo incluir uma extensão de reunião, certifique-se de que ela siga essas diretrizes.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [Diretrizes de design do módulo de tarefas do Teams](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

### <a name="pre--and-post-meeting-experience"></a>Experiência pré e pós-reunião

* As telas de pré e pós-reunião devem aderir às diretrizes gerais de design das guias. Para obter mais informações, consulte as [diretrizes de design do Teams](~/tabs/design/tabs.md).
* As guias não devem conter rolagem horizontal.
* As guias devem conter um layout organizado ao exibir vários itens. Por exemplo, mais de 10 enquetes ou pesquisas. Consulte um [exemplo de layout](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Seu aplicativo deve notificar aos usuários quando os resultados de uma pesquisa ou enquete forem exportados, declarando: "Resultados baixados com sucesso".

### <a name="in-meeting-experience"></a>Experiência na reunião

* Os aplicativos só devem usar um tema escuro durante as reuniões. Para obter mais informações, consulte as [diretrizes de design do Teams](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming).
* Uma dica de ferramenta deve exibir o nome do aplicativo ao passar o mouse sobre o ícone do aplicativo durante as reuniões.
* As extensões de mensagens devem funcionar da mesma forma durante as reuniões, assim como fora delas.

### <a name="in-meeting-tabs"></a>Guias na reunião

* Deve responder. Certifique-se de manter o preenchimento e o tamanho dos componentes.
* Deve ter um botão voltar se houver mais de uma camada de navegação.
* Não deve incluir mais de um botão de dispensar ou fechar. Isso pode confundir os usuários, pois já existe um botão de cabeçalho interno para dispensar a guia.
* Não deve conter rolagem horizontal.

### <a name="in-meeting-dialogs"></a>Caixas de diálogo na reunião

* Deve ser usado com moderação e em cenários que sejam leves e orientados para tarefas.
* Deve exibir o conteúdo em uma única coluna e não possuir vários níveis de navegação.
* Não deve usar módulos de tarefa.
* Deve alinhar-se ao centro do estágio da reunião.
* Deve ser ignorado quando um usuário seleciona um botão ou executa uma ação.

## <a name="notifications"></a>Notificações

Se o seu aplicativo usa as [APIs de feed de atividades fornecidas pelo Microsoft Graph](/graph/teams-send-activityfeednotifications), certifique-se de seguir as seguintes diretrizes.

### <a name="general"></a>Geral

* Todos os gatilhos de notificação especificados nas suas configurações de aplicativo devem receber uma notificação no aplicativo.
* As notificações devem ser localizadas de acordo com os idiomas suportados configurados no seu aplicativo.
* As notificações devem ser exibidas em cinco segundos a partir da ação do usuário.

### <a name="avatars"></a>Avatares

* O avatar de notificação deve corresponder ao ícone de cor do aplicativo.
* As notificações iniciadas por um usuário devem incluir o avatar do usuário.

### <a name="spamming"></a>Spam

* Os aplicativos não devem enviar mais de 10 notificações por minuto para um usuário.
* Os bots e o feed de atividades não devem acionar notificações duplicadas.
* As notificações devem fornecer valor aos usuários e não devem ser usadas em eventos triviais ou irrelevantes.

### <a name="navigation-and-layout"></a>Navegação e layout

* As notificações devem aderir ao layout e à experiência do feed de atividades do Teams.
* Ao selecionar uma notificação, o usuário deve ser direcionado ao conteúdo relevante no Teams, e não retirado da experiência do Teams.

## <a name="advertising"></a>Publicidade

Os aplicativos não devem exibir publicidade, incluindo anúncios dinâmicos, banners e anúncios em mensagens.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma conta do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
