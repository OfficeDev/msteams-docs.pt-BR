---
title: Microsoft Teams diretrizes de validação de lojas
description: Descreve as diretrizes que todos os aplicativos submetidos à loja de Teams (AppSource) devem seguir.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 4daa8b027d7525f0fb3223c2000eee301043398a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565134"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Microsoft Teams diretrizes de validação de lojas

Seguir essas diretrizes aumenta a probabilidade de seu aplicativo passar pelo processo de envio de Microsoft Teams loja. Essas diretrizes específicas Teams complementam as [políticas de certificação de marketplace comercial](/legal/marketplace/certification-policies) da Microsoft e são atualizadas frequentemente para refletir novos recursos, feedback do usuário e mudanças nas regras de negócios.

> [!NOTE]
> Algumas diretrizes podem não ser aplicáveis ao seu aplicativo. Por exemplo, se o seu aplicativo não incluir um bot, você pode ignorar as diretrizes relacionadas ao bot.

## <a name="10-value-proposition"></a>1.0 Proposta de valor

### <a name="11-app-name"></a>1.1 Nome do aplicativo

O nome de um aplicativo desempenha um papel fundamental na forma como os usuários o descobrem na loja. Lembre-se dos seguintes nomes de aplicativos:

* O nome deve incluir termos relevantes para seus usuários.
* Nomes dos principais recursos Teams&#8212;como **Chat,** **Contatos,** **Calendário,** **Chamadas**, **Arquivos**, **Atividade**, **Teams**, **Aplicativos** e **Ajuda**&#8212;não devem ser incluídos no nome do seu aplicativo.
* Substantivos comuns devem ser prefixados ou sufixos com o nome do desenvolvedor (por exemplo, **Contoso Tasks** em vez de **Tarefas**).
* Não deve usar **Teams** ou outros nomes de produtos da Microsoft que possam falsamente indicar co-branding ou co-venda. (Para obter mais informações sobre o referenciamento de software, produtos e serviços da Microsoft, consulte as [Diretrizes de Marcas e Marcas da Microsoft](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)).
* Se o seu aplicativo faz parte de uma parceria oficial com a Microsoft, o nome do seu aplicativo deve vir primeiro (por exemplo, **Contoso Connector para Microsoft Teams**).
* Não deve copiar o nome de um aplicativo listado na loja ou outra oferta no mercado comercial.
* Não deve conter termos profanos ou depreciativos. O nome também não deve incluir linguagem racial ou culturalmente insensível.
* Deve ser único. Por exemplo, você não pode listar vários aplicativos para diferentes regiões com o mesmo nome e funcionalidade.

### <a name="12-suitable-for-workplace-consumption"></a>1.2 Adequado para o consumo no local de trabalho

O conteúdo do aplicativo deve ser adequado para o consumo geral no local de trabalho e respeitar todas as restrições listadas nas políticas de certificação de mercado comercial. Conteúdo relacionado à religião, política, jogo e entretenimento prolongado é proibido. Para obter mais informações, consulte as [políticas de certificação de marketplace comercial.](/legal/marketplace/certification-policies#10010-inappropriate-content)

Seu aplicativo deve facilitar a colaboração em grupo, melhorar a produtividade de um indivíduo ou ambos. Os aplicativos destinados à união e à socialização da equipe devem ser colaborativos e projetados para vários participantes. Esses tipos de aplicativos também não devem exigir um investimento de tempo substancial ou impactar perceptivamente a produtividade.

### <a name="13-similar-platforms-and-services"></a>1.3 Plataformas e serviços similares

Os aplicativos devem se concentrar na experiência Teams e não incluir os nomes, ícones ou imagens de outras plataformas ou serviços de colaboração baseados em chat semelhantes, a menos que seu aplicativo forneça interoperabilidade específica.

### <a name="14-feature-names"></a>1.4 Nomes de recursos

Os nomes dos recursos do aplicativo em botões e outros textos de Interface do Usuário não devem entrar em conflito com a terminologia reservada para Teams e outros produtos da Microsoft. Por exemplo, **iniciar a reunião,** **fazer chamada** ou iniciar **o chat**. Inclua o nome do seu aplicativo se você não puder evitar completamente isso, como **a reunião do Start Contoso** em vez de começar a **reunião**.

## <a name="20-security"></a>2.0 Segurança

### <a name="21-microsoft-365-app-compliance-program"></a>2.1 Microsoft 365 Programa de Conformidade de Aplicativos

O [programa de conformidade de aplicativos Microsoft 365](/microsoft-365-app-certification/overview) tem o objetivo de ajudar as organizações a avaliar e gerenciar riscos, avaliando informações de segurança e conformidade sobre seu aplicativo. Se você estiver publicando um aplicativo para a loja Teams, você deve completar os seguintes níveis do programa:

* [Publisher Verificação](/azure/active-directory/develop/publisher-verification-overview): Ajuda administradores e usuários finais a entender a autenticidade dos desenvolvedores de aplicativos que integram com o plataforma de identidade da Microsoft. Quando concluído, um crachá azul "verificado" é exibido no diálogo de consentimento Azure Active Directory (Azure AD) e outras telas. Para obter mais informações, consulte [perguntas frequentes,](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions) [como marcar seu aplicativo como editor verificado](/azure/active-directory/develop/mark-app-as-publisher-verified)e [solucionar problemas de verificação do editor](/azure/active-directory/develop/troubleshoot-publisher-verification).
* [Publisher Attestation](/microsoft-365-app-certification/docs/attestation): Um processo no qual você compartilha informações gerais, de manipulação de dados e segurança e conformidade para ajudar potenciais clientes a tomar decisões informadas sobre o uso do seu aplicativo.

> [!NOTE]
> Se você está enviando um aplicativo que não foi listado anteriormente, você não pode completar oficialmente Publisher Attestation até que seu aplicativo esteja na loja Teams. Se você estiver atualizando um aplicativo listado, complete Publisher Attestation antes de enviar a versão mais recente do aplicativo.

### <a name="22-bots"></a>2.2 Bots

Para aplicativos que usam o Microsoft Azure Bot Service (como bots e extensões de mensagens), você deve seguir todos os requisitos definidos nos [Termos de Serviços Online da](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)Microsoft .

Os bots devem sempre pedir permissão para carregar um arquivo e exibir uma mensagem de confirmação após o upload do arquivo.

### <a name="23-external-domains"></a>2.3 Domínios externos

Na maioria dos casos, você não deve incluir domínios fora do controle da sua organização (incluindo curingas) e serviços de tunelamento nas configurações de domínio do seu aplicativo. As seguintes exceções incluem:

* Se o aplicativo usar o OAuthCard do Azure Bot Service, você deve incluir `token.botframework.com` como um domínio válido ou o botão Sinal de **entrar** não funcionará.
* Se o seu aplicativo depender de SharePoint, você pode incluir a raiz associada SharePoint site como um domínio válido usando a `{teamSiteDomain}` propriedade de contexto.

### <a name="24-authentication"></a>2.4 Autenticação

Para obter informações sobre como implementar a autenticação do aplicativo, consulte [autenticação em Teams](~/concepts/authentication/authentication.md).

#### <a name="241-authenticating-with-external-services"></a>2.4.1 Autenticação com serviços externos

Lembre-se do seguinte se o aplicativo autentica os usuários com um serviço externo.

* **Faça login, saia e inscreva experiências:**
  * Os aplicativos que dependem de contas ou serviços externos devem fornecer login, entrar, entrar e inscrever experiências claras e simples.
  * Quando um usuário se inscrever, ele deve sair apenas do aplicativo e permanecer conectado ao Teams.
* **Experiências de compartilhamento de conteúdo**: Aplicativos que requerem autenticação com um serviço externo para compartilhar conteúdo em canais Teams devem declarar claramente na documentação de ajuda (ou recursos similares) como desconectar ou descompartilhe conteúdo se esse recurso for suportado no serviço externo. Isso não significa que a capacidade de descompartilho deve estar presente em seu aplicativo Teams.

#### <a name="242-government-community-cloud-listings"></a>2.4.2 Nuvem da Comunidade Governamental listagens

Para distribuir seu aplicativo para usuários Nuvem da Comunidade Governamental (GCC), evitando listagens duplicadas na loja de Teams, o processo de autenticação deve identificar e encaminhar os usuários para uma URL específica ou esperada de GCC.

### <a name="25-sensitive-content"></a>2.5 Conteúdo sensível

Seu aplicativo não deve postar dados confidenciais, como dados de cartão de crédito ou instrumento de pagamento financeiro. O aplicativo também não deve exibir saúde, rastreamento de contato ou outras informações pessoalmente identificáveis (PII) para um público que não pretende visualizar esse conteúdo.

Alerte os usuários antes que seu aplicativo baixe quaisquer arquivos ou executáveis (.exe) na máquina ou ambiente do usuário.

### <a name="26-financial-information"></a>2.6 Informações financeiras

Os aplicativos não devem pedir aos usuários que façam pagamentos dentro da interface Teams. Os detalhes do instrumento financeiro não devem ser transmitidos aos usuários através de uma interface de bot.

Você só pode vincular a serviços de pagamento externos seguros se você fizer a divulgação apropriada em seus termos de uso, política de privacidade ou qualquer página de perfil ou site antes que o usuário concorde em usar o aplicativo.

Os aplicativos rodando na versão iOS ou Android do Teams devem seguir as seguintes diretrizes:

* Os aplicativos não devem incluir compras no aplicativo, ofertas de teste ou interface do usuário que visa upsell para versões pagas ou links para lojas online onde os usuários podem comprar ou adquirir outros conteúdos, aplicativos ou complementos.
* Se o seu aplicativo exigir uma conta, os usuários devem ser capazes de se inscrever em uma conta sem custo. É proibido o uso do termo **livre** ou **livre conta.**
* Você pode determinar se uma conta está ativa indefinidamente ou por tempo limitado, mas se a conta expirar, nenhuma interface do usuário, texto ou links indicando a necessidade de pagamento pode ser mostrada.
* A política de privacidade e os termos de uso do seu aplicativo devem estar livres de qualquer interface do usuário ou links relacionados ao comércio.

## <a name="30-general-functionality-and-performance"></a>3.0 Funcionalidade geral e desempenho

### <a name="31-launching-external-functionality"></a>3.1 Lançamento de funcionalidade externa

Os aplicativos não devem tirar os usuários de Teams para os principais cenários de usuários. O conteúdo e as interações do aplicativo podem ocorrer dentro de Teams recursos, como bots, cartões e módulos de tarefas.

Você deve vincular os usuários em algum lugar Teams e não a um site ou aplicativo externo. Para cenários que requerem funcionalidade externa, seu aplicativo deve ter permissão explícita do usuário para iniciar essa funcionalidade.

### <a name="32-compatibility"></a>3.2 Compatibilidade

Os aplicativos devem estar totalmente funcionais nos seguintes sistemas operacionais e navegadores:

* Microsoft Windows 7 e depois
* macOS 10.10 e posterior
* Microsoft Edge 12 e posterior
* Mozilla Firefox 47.0 e depois
* Google Chrome 51.0 e posterior
* iOS 9.0 e posterior
* Android 4.4 e posterior

### <a name="33-response-time"></a>3.3 Tempo de resposta

Teams aplicativos devem responder dentro de um prazo razoável, que varia dependendo da capacidade.

* As guias devem responder dentro de três segundos ou exibir uma mensagem de carregamento ou aviso.
* Os bots devem responder aos comandos do usuário dentro de dois segundos ou exibir um indicador de digitação.
* As extensões de mensagens devem responder aos comandos do usuário dentro de cinco segundos.
* As notificações devem ser exibidas dentro de cinco segundos após a ação do usuário.

## <a name="40-app-package-and-store-listing"></a>4.0 Lista de pacotes de aplicativos e lojas

Os pacotes de aplicativos devem ser corretamente formatados e incluir todas as informações e componentes necessários.

### <a name="41-app-manifest"></a>4.1 Manifesto de aplicativos

O manifesto do aplicativo Teams define as configurações do seu aplicativo.

* Seu manifesto deve estar de acordo com o último esquema manifesto. Para obter informações, consulte a [referência manifesto.](~/resources/schema/manifest-schema.md)
* Se o seu aplicativo incluir uma extensão de bot ou mensagens, seu manifesto deve ser consistente com metadados do Bot Framework, incluindo nome do bot, logotipo, link de política de privacidade e termos de link de serviço.
* Se o seu aplicativo usar Azure Active Directory (Azure AD) para autenticação, inclua o ID do Aplicativo Azure (cliente) no manifesto. Para obter mais informações, consulte a [referência manifesto](~/resources/schema/manifest-schema.md#webapplicationinfo).

### <a name="42-app-icons"></a>4.2 Ícones do aplicativo

Ícones são um dos principais elementos que as pessoas vêem ao navegar na loja Teams. Seus ícones devem comunicar a marca e o propósito do seu aplicativo, ao mesmo tempo em que adsuem aos seguintes requisitos:

* Seu pacote de aplicativos deve incluir duas versões PNG do ícone do aplicativo: um ícone de cor e um ícone de contorno.
* A versão colorida do seu ícone é exibida na maioria dos cenários Teams e deve ser de 192x192 pixels. Seu símbolo de ícone (96x96 pixels) pode ser qualquer cor ou cor, mas deve sentar-se em um fundo quadrado sólido ou totalmente transparente.
* A versão de contorno do ícone é exibida quando seu aplicativo está em uso e "içado" na barra de aplicativos no lado esquerdo da Teams e quando um usuário fixa a extensão de mensagens do seu aplicativo. Deve ser 32x32 pixels e pode ser branco com um fundo transparente ou transparente com fundo branco (nenhuma outra cor é permitida). O ícone não deve ter nenhum preenchimento extra em torno do símbolo.
* Ícones de tamanho e formato corretos devem ser incluídos no pacote do aplicativo. Os ícones também devem coincidir com o que é enviado com os metadados de listagem da loja.

Para obter mais informações, práticas recomendadas e exemplos, consulte as diretrizes de [ícones](~/concepts/build-and-test/apps-package.md#app-icons)de aplicativos Teams .

### <a name="43-app-descriptions"></a>4.3 Descrições do aplicativo

Você deve ter uma descrição curta e longa do seu aplicativo. As descrições nas configurações do aplicativo e no Partner Center devem ser as mesmas.

As descrições não devem ser diretas ou por meio de insinuações depreciando outra marca (microsoft de propriedade ou não). Certifique-se de que sua descrição não inclua alegações que não podem ser comprovadas (por exemplo, "Aumento garantido de 200% na eficiência").

#### <a name="431-short-description"></a>4.3.1 Descrição curta

Uma descrição curta é um resumo conciso do seu aplicativo que destaca sua proposta de valor e é direcionado ao seu público-alvo.

**Faça:**

* Mantenha a descrição curta para uma frase.
* Fale primeiro as informações mais importantes.
* Inclua palavras-chave que os clientes provavelmente procurarão.

**Não faça:**

* Repita o nome do aplicativo.
* Use o **aplicativo** de palavras na descrição curta.

#### <a name="432-long-description"></a>4.3.2 Descrição longa

A longa descrição pode fornecer uma narrativa envolvente que destaca a proposta de valor do seu aplicativo, o público principal e a indústria-alvo. Embora esta descrição possa ser de até 4.000 caracteres, a maioria dos usuários só lerá entre 300-500 palavras.

**Faça:**

* Use [o Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) para formatar sua descrição.
* Use voz ativa e fale diretamente com os usuários. Por exemplo, *você pode...*.
* Liste recursos com pontos de bala, por isso é mais fácil digitalizar a descrição.
* Descreva claramente limitações, condições ou exceções à funcionalidade, recursos e entregas descritos na listagem e materiais relacionados antes que o usuário instale seu aplicativo. Os recursos Teams que seu aplicativo suporta devem estar relacionados com as principais funções que sua listagem descreve.
* Inclua um link de ajuda ou suporte.
* Consulte **Microsoft 365** em vez de **Office 365**.
* Se você precisar **fazer** referência Teams, escreva a primeira referência como **Microsoft Teams**. As referências subsequentes podem ser encurtadas para **Teams**.
* Use o idioma a seguir ao descrever como o aplicativo funciona com Teams (ou Microsoft 365):
  * "... trabalha com Microsoft Teams.
  * "... trabalhando com Microsoft Teams.
  * "... dentro Microsoft Teams.
  * "... para Microsoft Teams.

**Não faça:**

* Exceda 500 palavras.
* Abreviar a **Microsoft** como **MS** ou **MSFT**.
* Indique que o aplicativo é uma oferta da Microsoft, incluindo o uso de slogans ou slogans da Microsoft.
* Use marcas com direitos autorais que você não possui.
* Incluem erros de digitação, erros gramaticais e capitalizações desnecessárias (por exemplo, **Usuários** em vez de **usuários**).
* Inclua links para AppSource.
* Use o idioma a seguir, a menos que você seja um parceiro microsoft certificado:
  * "... integrado com Microsoft Teams"
  * "... integra-se com ..."
  * "... construído para ..."
  * "... construído em ..."
  * "... funciona ..."
  * "... habilitado por ..."
  * "... certificado para ..."
  * "... desenvolvido para ..."
  * "... projetado para ..."

### <a name="44-screenshots"></a>4.4 Capturas de tela

As capturas de tela fornecem uma visualização visual proeminente do seu aplicativo para complementar o nome do aplicativo, o ícone e as descrições. Lembre-se dos seguintes capturas de tela:

* Você pode ter até cinco capturas de tela por listagem.
* Os tipos de arquivos suportados incluem PNG, JPEG e GIF.
* As dimensões devem ser de 1366x768 pixels.
* Tamanho máximo de 1.024 KB.

**Faça:**

* Concentre-se nos recursos do seu aplicativo (por exemplo, como as pessoas podem se comunicar com seu bot).
* Inclua conteúdo que represente com precisão seu aplicativo.
* Use texto criteriosamente.
* Armação de capturas de tela com uma cor que reflete sua marca e inclui conteúdo de marketing, semelhante ao exemplo de [listagem do Freshdesk](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) (os requisitos de dimensão se aplicam a toda a imagem e não apenas à captura de tela).

**Não faça:**

* Mostre dispositivos específicos, como telefones ou laptops.
* Exibir chrome ou interface do usuário que não está no seu aplicativo.
* Capture qualquer interface do Teams ou interface do navegador nas capturas de tela.
* Inclua maquetes que refletem imprecisamente a interface do usuário real do seu aplicativo, como mostrar que seu aplicativo está sendo usado fora de Teams.

> [!TIP]
> Um vídeo pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Um vídeo também é a primeira coisa que os usuários vêem em sua listagem (por padrão, um vídeo é exibido antes das capturas de tela). Para obter mais informações, consulte [criar um vídeo para a listagem da sua loja](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

### <a name="45-privacy-policy"></a>4.5 Política de privacidade

A política de privacidade pode ser específica para o seu aplicativo de Teams ou uma política geral para todos os seus serviços.

* Se você usa um modelo genérico de política de privacidade, você deve referenciar **serviços, aplicativos** e  **plataformas** para incluir seu aplicativo Teams e seu serviço ou site.
* Deve incluir como você lida com o armazenamento, retenção e exclusão de dados do usuário. Você também deve descrever os controles de segurança que você usa para proteção de dados.
* Deve incluir suas informações de contato.
* Não devem conter URLs que estão quebrados ou para fins beta ou de estadiamento.
* Não deve incluir links para AppSource.

### <a name="46-terms-of-use"></a>4.6 Termos de uso

Seus termos de uso devem ser específicos e aplicáveis à sua oferta.

### <a name="47-support-links"></a>4.7 Links de suporte

Os URLs de suporte do seu aplicativo não devem exigir autenticação. Por exemplo, os usuários não devem fazer login para entrar em contato com você.

### <a name="48-localization"></a>4.8 Localização

Se o aplicativo suportar a localização, o pacote do aplicativo deve incluir um arquivo com traduções de idioma que são exibidas com base na configuração Teams idioma. O arquivo deve estar em conformidade com o esquema de localização Teams. Para obter mais informações, consulte o [esquema de localização Teams](~/concepts/build-and-test/apps-localization.md).

## <a name="50-tabs"></a>5.0 Guias

Se o seu aplicativo incluir uma guia, certifique-se de que ele adere a essas diretrizes.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes de design de guias Teams](~/tabs/design/tabs.md).

### <a name="51-setup"></a>Configuração 5.1

* A configuração da guia não deve beco sem saída a um novo usuário. Forneça uma mensagem sobre como completar a ação ou o fluxo de trabalho.
* A autenticação deve acontecer durante a configuração da guia e não depois.

### <a name="52-views"></a>5.2 Visualizações

* A área de tela de login não deve usar logotipos grandes ou exibir uma página web inteira.
* O conteúdo pode ser simplificado dividindo-o em várias guias.
* As guias não devem ter um cabeçalho duplicado. Remova o logotipo do iframe, já que a estrutura da guia já exibe o ícone e o nome do aplicativo.

### <a name="53-navigation"></a>5.3 Navegação

* As guias não devem ter mais de três níveis de navegação.
* As guias não devem fornecer navegação que entre em conflito com a navegação Teams primária.
* As páginas secundárias e terciárias em uma guia devem ser abertas em uma exibição nível dois e nível três na área principal da guia, que é navegada através de migalhas de pão ou navegação esquerda. Você também pode incluir os seguintes componentes para ajudar a navegação de guias:
    * Botões traseiros
    * Cabeçalhos de página
    * Menus de hambúrguer
* A guia não deve ter pergaminho horizontal.
* Links profundos nas guias não devem vincular a uma página da Web externa, mas em algum lugar dentro de Teams. Por exemplo, módulos de tarefa ou outras guias.
* As guias não devem permitir que os usuários naveguem fora Teams para a experiência principal do aplicativo.

### <a name="54-usability"></a>5.4 Usabilidade

* As guias devem fornecer valor além de apenas hospedar um site existente.
* Os usuários devem ser capazes de desfazer sua última ação na guia.
* Guias em um contexto pessoal podem agregar conteúdo a partir de instâncias compartilhadas do aplicativo.
* As guias devem ser responsivas aos Teams temas. Quando um usuário altera o tema, o tema do aplicativo deve refletir a seleção.
* As guias devem usar componentes com estilo Teams, como fontes Teams, rampas de tipo, paletas de cores, sistema de grade, movimento, tom de voz e assim por diante sempre que possível.
* Você deve incluir uma **guia Configurações.**
* As guias devem seguir Teams design de interação, como, navegação na página, posição e uso de diálogos, hierarquias de informações e assim por diante sempre que possível.
* O conteúdo da guia no iframe não deve incluir recursos que imitam Teams recursos principais. Por exemplo, bots, extensões de mensagens, chamadas, reuniões e assim por diante.

> [!TIP]
>
> * Inclua um bot pessoal ao lado de uma guia pessoal.
> * Permitir que os usuários compartilhem conteúdo de sua guia pessoal.

## <a name="60-bots"></a>6.0 Bots

Se o seu aplicativo incluir um bot, certifique-se de que ele adere a essas diretrizes.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes de design de Teams bot](~/bots/design/bots.md).

### <a name="61-bot-commands"></a>6.1 Comandos de bot

Analisar a entrada do usuário e prever a intenção do usuário é difícil. Os comandos bot fornecem aos usuários um conjunto de palavras ou frases que seu bot entende para que eles (e seu bot) não precisem adivinhar.

* Listar comandos de bot suportados nas configurações do aplicativo é altamente recomendado. Esses comandos são exibidos na caixa de composição quando um usuário tenta enviar uma mensagem ao seu bot.
* Todos os comandos que o seu bot suporta devem funcionar corretamente, incluindo o comando **Oi,** **Olá** e **Ajuda.**

> [!TIP]
> Para bots pessoais, inclua uma guia **Ajuda** que descreva ainda mais o que seu bot pode fazer.

### <a name="62-bot-welcome-messages"></a>6.2 Mensagens de boas-vindas do Bot

* Os bots devem quase sempre enviar uma mensagem de boas-vindas durante a primeira execução. Para obter a melhor experiência, a mensagem deve incluir a proposta de valor do seu bot, como configurar o bot e descrever brevemente todos os comandos de bot suportados. Você pode exibir a mensagem usando uma placa adaptativa com botões para melhor usabilidade. Para obter mais informações, veja [como ativar uma mensagem de boas-vindas do bot](~/bots/how-to/conversations/send-proactive-messages.md).
* As mensagens de boas-vindas do bot em canais e chats são opcionais durante a primeira execução, especialmente se o bot estiver disponível para uso pessoal e realizar ações semelhantes. Se o seu bot enviar mensagens de boas-vindas, ele não deve enviá-las para os usuários individualmente (isso é considerado [spam](#63-bot-message-spamming)). A mensagem também deve mencionar a pessoa que adicionou o bot.
* Os bots somente de notificação devem enviar uma mensagem de boas-vindas que transmite que não responderá às mensagens dos usuários.

> [!TIP]
> Em mensagens de boas-vindas a usuários individuais, um passeio de carrossel pode fornecer uma visão geral eficaz do seu bot e de qualquer outro recurso do aplicativo. Incluindo botões, o let users try comandos bot é encorajado. Por exemplo, **crie uma tarefa**.

### <a name="63-bot-message-spamming"></a>6.3 Mensagem de bot spam

Os bots não devem enviar spam aos usuários enviando várias mensagens em sucessão curta.

* **Mensagens de bot em canais e chats**: Não faça spam aos usuários criando postagens separadas. Crie uma única postagem com respostas no mesmo segmento.
* **Mensagens de bot em aplicativos pessoais**: Não envie várias mensagens em rápida sucessão. Envie uma mensagem com informações completas. Evite conversas de várias voltas para completar um único fluxo de trabalho. Em vez disso, considere usar um formulário (ou módulo de tarefa) para coletar todas as entradas de um usuário ao mesmo tempo.
* **Mensagens de boas-vindas**: Repetir a mesma mensagem de boas-vindas em intervalos regulares não é permitido e considerado spam. Por exemplo, quando um novo membro é adicionado a uma equipe, não faça spam aos outros membros com uma mensagem de boas-vindas. Envie uma mensagem para o novo membro pessoalmente.

### <a name="64-bot-notifications"></a>6.4 Notificações de bot

As notificações do bot devem incluir conteúdo relevante para o escopo definido para o bot (equipe, chat ou pessoal).

### <a name="65-bots-and-adaptive-cards"></a>6.5 Bots e Cartões Adaptativos

Cartões adaptativos são uma maneira altamente recomendada de exibir mensagens de bot. Suas cartas devem ser leves e incluem apenas 1-3 ações. Se você precisar exibir mais conteúdo, considere usar um módulo de tarefa ou guia.

Veja os seguintes recursos para obter mais informações:

* [Criar Cartões Adaptáveis](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Referência de cartões](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

## <a name="70-messaging-extensions"></a>Extensões de mensagens 7.0

Se o seu aplicativo incluir uma extensão de mensagens, certifique-se de que ele adere a essas diretrizes.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes de design de extensão de mensagens Teams](~/messaging-extensions/design/messaging-extension-design.md).

### <a name="71-action-commands"></a>7.1 Comandos de ação

As extensões de mensagens baseadas em ação devem fazer o seguinte:

* Permitir que os usuários acionem ações em uma mensagem sem completar etapas intermediárias, como fazer login.
* Passe o contexto da mensagem para o próximo estado de trabalho.

### <a name="72-preview-links-link-unfurling"></a>7.2 Links de visualização (desenrolar de link)

As extensões de mensagens devem visualizar links reconhecidos na caixa de composição Teams. Não adicione domínios que estejam fora do seu controle (URLs absolutos ou curingas). Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido. Domínios de nível superior também são proibidos (por exemplo, `*.com` ou `*.org` ).

### <a name="73-search-commands"></a>7.3 Comandos de pesquisa

* As extensões de mensagens baseadas em pesquisa devem fornecer texto que ajude os usuários a pesquisar efetivamente.
* @mention executáveis devem ser claros, fáceis de entender e legíveis.

## <a name="80-task-modules"></a>8.0 Módulos de tarefa

Um módulo de tarefa deve incluir um ícone e o nome curto do aplicativo com o qual está associado.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes de design do módulo de tarefas Teams](~/task-modules-and-cards/task-modules/design-teams-task-modules.md).

## <a name="90-meeting-extensions"></a>9.0 Extensões de reunião

Se o seu aplicativo incluir uma extensão de reunião, certifique-se de que ele adere a essas diretrizes.

> [!TIP]
> Para obter informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte o [Teams atender às diretrizes de projeto de extensão](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

### <a name="91-pre--and-post-meeting-experience"></a>9.1 Experiência pré e pós-reunião

* As telas pré e pós-reunião devem seguir as diretrizes gerais de design de guias. Para obter mais informações, consulte as [diretrizes de design Teams](~/tabs/design/tabs.md).
* As guias não devem ter rolagem horizontal.
* As guias devem ter um layout organizado ao exibir vários itens. Por exemplo, mais de 10 pesquisas ou pesquisas. Veja um [layout de exemplo](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Seu aplicativo deve notificar os usuários quando os resultados de uma pesquisa ou enquete são exportados afirmando: "Resultados baixados com sucesso".

### <a name="92-in-meeting-experience"></a>9.2 Experiência de encontro

* Os aplicativos só devem usar um tema escuro durante as reuniões. Para obter mais informações, consulte as [diretrizes de design Teams](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming).
* Uma dica de ferramenta deve exibir o nome do aplicativo ao pairar sobre o ícone do aplicativo durante as reuniões.
* As extensões de mensagens devem funcionar da mesma forma durante as reuniões que fazem fora das reuniões.

### <a name="93-in-meeting-tabs"></a>9.3 Guias de reunião

* Deve ser responsivo. Certifique-se de manter o preenchimento e os tamanhos dos componentes.
* Deve ter um botão traseiro se houver mais de uma camada de navegação.
* Não deve incluir mais de um botão de descarte ou fechamento. Isso pode confundir os usuários, já que já existe um botão de cabeçalho embutido para descartar a guia.
* Não deve ter rolagem horizontal.

### <a name="94-in-meeting-dialogs"></a>9.4 Diálogos em reunião

* Deve ser usado com moderação e para cenários leves e orientados para tarefas.
* Deve exibir conteúdo em uma única coluna e não ter vários níveis de navegação.
* Não deve usar módulos de tarefa.
* Deve estar alinhado com o centro da fase de reunião.
* Deve ser dispensado assim que um usuário selecionar um botão ou realizar uma ação.

## <a name="100-notifications"></a>10.0 Notificações

Se o aplicativo usar as [APIs de alimentação de atividade fornecidas pela Microsoft Graph,](/graph/teams-send-activityfeednotifications)certifique-se de que ele adere às seguintes diretrizes.

### <a name="101-general"></a>10.1 Geral

* Todos os gatilhos de notificação especificados nas configurações do aplicativo devem receber uma notificação no aplicativo.
* As notificações devem ser localizadas de acordo com os idiomas suportados configurados para o seu aplicativo.
* As notificações devem ser exibidas dentro de cinco segundos após a ação do usuário.

### <a name="102-avatars"></a>10.2 Avatares

* O avatar de notificação deve corresponder ao ícone de cor do seu aplicativo.
* As notificações desencadeadas por um usuário devem incluir o avatar do usuário.

### <a name="103-spamming"></a>10.3 Spam

* Os aplicativos não devem enviar mais de 10 notificações por minuto para um usuário.
* Os bots e o feed de atividade não devem acionar notificações duplicadas.
* As notificações devem fornecer algum valor aos usuários e não serem usadas para eventos triviais ou irrelevantes.

### <a name="104-navigation-and-layout"></a>10.4 Navegação e layout

* As notificações devem aderir ao layout e experiência do feed de atividades Teams.
* Ao selecionar uma notificação, o usuário deve ser direcionado para conteúdo relevante dentro de Teams e não retirado da experiência Teams.

## <a name="110-advertising"></a>11.0 Publicidade

Os aplicativos não devem exibir publicidade, incluindo anúncios dinâmicos, anúncios de banner e anúncios em mensagens.

## <a name="see-also"></a>Confira também

[4.0 Lista de pacotes de aplicativos e lojas](#40-app-package-and-store-listing)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma conta do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
