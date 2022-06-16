---
title: Diretrizes de validação da loja do Microsoft Teams
description: Neste artigo, você terá as diretrizes que todos os aplicativos enviados à loja do Teams (AppSource) devem seguir.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: 316105d9ea6010094328ad7d204cfb765aecc022
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123840"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Diretrizes de validação da loja do Microsoft Teams

Seguir essas diretrizes aumenta as chances de seu aplicativo ser aprovado no processo de envio à store do Microsoft Teams. As diretrizes específicas do Teams complementam as [políticas de certificação do marketplace comercial](/legal/marketplace/certification-policies) da Microsoft e são atualizadas com frequência para refletir novos recursos, comentários do usuário e alterações nas regras de negócios.

> [!NOTE]
>
> * É possível que algumas diretrizes não sejam pertinentes ao seu aplicativo. Por exemplo, se seu aplicativo não incluir um bot, você poderá ignorar as diretrizes relacionadas ao bot.
> * Cruzamos essas diretrizes com as políticas de certificação comercial da Microsoft e adicionamos o que fazer e o que não fazer com exemplos de cenários de aprovação ou reprovação encontrados em nosso processo de validação.
> * Determinadas diretrizes são marcadas como *Correção Obrigatória*. Se o envio do aplicativo não atender a essas diretrizes obrigatórias, você receberá um relatório de falha conosco com etapas para atenuar. O envio do aplicativo passará na Validação da loja do Microsoft Teams somente depois que você corrigir os problemas.
> * Outras diretrizes são marcadas como *Correção sugerida*. Para uma experiência de usuário ideal, sugerimos que você corrija os problemas, no entanto, seu envio de aplicativo não será impedido de publicar na loja do Teams, se você optar por não corrigir os problemas.

:::row:::
   :::column:::
      :::image type="content" source="../../../../assets/icons/value-proposition.png" alt-text="value-proposition-teams" link="#value-proposition" border="false":::
   :::column-end:::
   :::column span="":::
     :::image type="content" source="../../../../assets/icons/security.png" alt-text="security-store" link="#security" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/function.png" alt-text="functionality" link="#general-functionality-and-performance" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/package.png" alt-text="app-package" link="#app-package-and-store-listing" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/saas-offer.PNG" alt-text="saas" link="#apps-linked-to-saas-offer" border="false":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/tab.png" alt-text="tab-teams" link="#tabs" border="false":::
   :::column-end:::
   :::column:::
      :::image type="content" source="../../../../assets/icons/bot.png" alt-text="bot-teams" link="#bots-1" border="false":::
   :::column-end:::
   :::column span="":::
     :::image type="content" source="../../../../assets/icons/messaging-extension.png" alt-text="messaging" link="#message-extensions" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/task-module.png" alt-text="task-module-teams" link="#task-modules" border="false":::
   :::column-end:::
     :::column span="":::
      :::image type="content" source="../../../../assets/icons/meeting.png" alt-text="meeting-extension" link="#meeting-extensions" border="false":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/empty.png" alt-text="empty-2" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/notifications.png" alt-text="teams-notification" link="#notifications" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/microsoft-365.png" alt-text="microsoft" link="#microsoft-365-app-compliance-program" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/advertising.png" alt-text="advertising-teams" link="#advertising" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/empty.png" alt-text="empty-1" border="false":::
   :::column-end:::
:::row-end:::

## <a name="value-proposition"></a>Proposta de valor

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false"::: Esta seção está alinhada com a [Política de certificação comercial da Microsoft número 1140.1](/legal/marketplace/certification-policies#11401-value-proposition-and-offer-requirements) e fornece orientações adicionais aos desenvolvedores de aplicativos do Microsoft Teams sobre a proposta de valor das suas ofertas.

### <a name="app-name"></a>Nome do aplicativo

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false"::: Esta seção está alinhada com a [ política de certificação comercial da Microsoft número 1140.1.1 ](/legal/marketplace/certification-policies#114011-app-name) e fornece orientações adicionais aos desenvolvedores sobre como nomear seus aplicativos.
<br></br>
<details><summary>Expanda para saber mais</summary>

O nome de um aplicativo desempenha um papel fundamental na forma como os usuários o descobrem na loja. Use as seguintes diretrizes para nomear um aplicativo:

* O nome deve incluir termos relevantes aos seus usuários.
* Os nomes dos principais recursos do Teams não devem ser incluídos no nome do aplicativo, como:  
  * **Chat**
  * **Contatos**
  * **Calendar**
  * **Chamadas**
  * **Files**
  * **Atividades**
  * **Aplicativos**
  * **Help**
* Prefixo ou sufixo substantivos comuns com o nome do desenvolvedor. Por exemplo, **Tarefas da Contoso** em vez de **Tarefas**.
* Não deve usar **Teams** ou outros nomes de produtos da Microsoft, como Excel, PowerPoint, Word, OneDrive, Microsoft Office SharePoint Online, OneNote, Azure, Surface, Xbox e assim por diante, que possam indicar falsamente co-branding ou venda conjunta. Para obter mais informações sobre como fazer referência a produtos e serviços de software da Microsoft, confira [Marca Registrada e Diretrizes da Marca Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
* Se o seu aplicativo faz parte de uma parceria oficial com a Microsoft, o nome do seu aplicativo deve vir primeiro. Por exemplo, **Conector da Contoso para Microsoft Teams**.
* Não é preciso copiar o nome de um aplicativo listado na loja ou em outra oferta no mercado comercial.
* Não deve conter termos profanos ou depreciativos. O nome também não deve incluir linguagem racial ou culturalmente insensível.
* Deve ser exclusivo. Se seu aplicativo (Contoso) estiver listado no repositório do Microsoft Teams e Microsoft AppSource e você quiser listar outro aplicativo específico para uma geografia, como Contoso México, seu envio deverá atender aos seguintes critérios:
  * Chame a funcionalidade específica da região do aplicativo no título, metadados, experiência do aplicativo de primeira resposta e seções de ajuda. Por exemplo, o título deve ser Contoso México. O título do aplicativo deve diferenciar claramente um aplicativo existente do mesmo desenvolvedor para evitar confusão para o usuário final.
  * Ao fazer o upload do pacote do aplicativo no Partner Center, selecione os **Mercados** certos onde o aplicativo estará disponível na seção **Disponibilidade**.

 > [!TIP]  
 > A marca do seu aplicativo na loja do Microsoft Teams e no Microsoft AppSource, incluindo o nome do aplicativo, nome do desenvolvedor, ícone do aplicativo, capturas de tela do Microsoft AppSource, vídeo, breve descrição e site da Web, separadamente ou em conjunto, não devem representar uma oferta oficial da Microsoft, a menos que seu aplicativo seja oficial Oferta 1P da Microsoft.

</details>

### <a name="suitable-for-workplace-consumption"></a>Adequado para o consumo no local de trabalho

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false"::: Esta seção está alinhada com a política de certificação comercial da Microsoft número [1140.1.2](/legal/marketplace/certification-policies#114012-workplace-appropriateness), [100.8](/legal/marketplace/certification-policies#1008-significant-value), e [100.10](/legal/marketplace/certification-policies#10010-inappropriate-content) e fornece orientações adicionais aos desenvolvedores sobre como criar aplicativos apropriados para o local de trabalho.
<br></br>
<details><summary>Expanda para saber mais</summary>

O conteúdo do aplicativo deve ser adequado para consumo geral no local de trabalho e seguir todas as restrições listadas nas políticas de certificação do mercado comercial. É proibido o conteúdo relacionado à religião, política, jogos de azar e entretenimento prolongado.

Seu aplicativo deve permitir a colaboração em grupo, melhorar a produtividade de um indivíduo ou ambos. Os aplicativos destinados à união e socialização da equipe devem ser colaborativos e projetados para vários participantes. Os aplicativos não devem exigir um investimento de tempo substancial de mais de 60 minutos por sessão ou afetar a produtividade.

</details>

### <a name="similar-platforms-and-services"></a>Plataformas e serviços semelhantes

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política de certificação comercial da Microsoft número 1140.1.3](/legal/marketplace/certification-policies#114013-other-platforms-and-services).

Os aplicativos devem se concentrar na experiência do Teams e não incluir nomes, ícones ou imagens de outras plataformas ou serviços de colaboração baseados em chat semelhantes no conteúdo do aplicativo ou nos metadados do aplicativo, a menos que o aplicativo forneça interoperabilidade específica.

### <a name="feature-names"></a>Nomes de recursos

Nomes de recursos de aplicativos em botões e outros textos de IU não devem ser duplicados com a terminologia reservada para Teams e outros produtos Microsoft. Por exemplo, **Iniciar reunião**, **Fazer chamadas** ou **Iniciar bate-papo**. Se necessário, inclua o nome do seu aplicativo, como **Iniciar reunião da Contoso**.

### <a name="authentication"></a>Autenticação

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false"::: Esta seção está alinhada com a [política de certificação comercial da Microsoft número1140.1.4 ](/legal/marketplace/certification-policies#114014-access-to-services) e fornece orientações aos desenvolvedores sobre como autenticar seus aplicativos com serviços externos.

Para obter mais informações sobre como implementar a autenticação de aplicativo, consulte [autenticação em Teams](~/concepts/authentication/authentication.md).
<br></br>
<details><summary>Expanda para saber mais</summary>

#### <a name="authenticating-with-external-services"></a>Autenticação com serviços externos

Se seu aplicativo autentica usuários com um serviço externo, siga estas diretrizes:

* **Entre, saia e inscreva-se em experiências**:
  * Os aplicativos que dependem de contas ou serviços externos devem fornecer uma experiência de entrada, saída e inscrição clara e simples.
  * Quando os usuários se desconectam, eles devem se desconectar apenas do aplicativo e permanecer conectados ao Teams.
  * Os aplicativos que dependem de contas ou serviços externos devem fornecer um caminho a seguir para que novos usuários se inscrevam ou contatem o editor do aplicativo para saber mais sobre os serviços e obter acesso aos serviços.
  O caminho a seguir deve estar disponível no manifesto do aplicativo, na descrição longa do AppSource e na experiência de primeira execução do aplicativo (mensagem de boas-vindas do bot, configuração da guia ou página de configuração).
  * Os aplicativos que exigem que o administrador do locatário conclua a configuração única devem chamar a dependência do administrador do locatário para configurar o aplicativo (antes que qualquer outro usuário locatário possa instalar e usar o aplicativo).  
  A dependência deve ser mencionada no manifesto do aplicativo, na descrição longa do AppSource, em todos os pontos de contato da primeira experiência de execução (mensagem de boas-vindas do bot, configuração da guia ou página de configuração), texto de ajuda conforme considerado necessário como parte da resposta do bot, extensão de composição ou conteúdo da guia estática.
  
* **Experiências de compartilhamento de conteúdo**: os aplicativos que requerem autenticação de um serviço externo para compartilhar conteúdo nos canais do Teams devem indicar claramente na documentação de ajuda (ou recursos semelhantes) como desconectar ou descompartilhar o conteúdo se esse recurso for compatível com o serviço externo. Isso não significa que a capacidade de descompartilhar o conteúdo deve estar presente no aplicativo Teams.

</details>

## <a name="security"></a>Segurança

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política de certificação comercial da Microsoft número 1140.3](/legal/marketplace/certification-policies#11403-security).

### <a name="financial-information"></a>Informações financeiras

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false"::: Esta seção está alinhada com a [política de certificação comercial da Microsoft número 1140.3.1](/legal/marketplace/certification-policies#114031-financial-transactions) e fornece orientações sobre a transmissão de informações financeiras na interface do Teams e notifica os desenvolvedores sobre cenários de pagamentos restritos na versão móvel (Android  e iOS) do aplicativo Teams.
<br></br>
<details><summary>Expanda para saber mais</summary>

Os aplicativos não devem pedir aos usuários que façam pagamentos na interface do Teams e transmitam informações financeiras aos usuários por meio de uma interface de bot.

:::image type="content" source="../../../../assets/images/submission/validation-financial-information-1.png" alt-text="validation-financial-info":::

Você pode fornecer um link para proteger serviços de pagamento externos apenas se divulgá-lo em seus termos de uso, política de privacidade, página de perfil ou site antes de o usuário concordar em usar o aplicativo.

Não facilite pagamentos por meio de um aplicativo de bens ou serviços proibidos pela [política geral número 100.10 Conteúdo impróprio](/legal/marketplace/certification-policies#10010-inappropriate-content).

Os aplicativos em execução na versão para iOS ou Android do Teams devem seguir as seguintes diretrizes:

* Os aplicativos não devem incluir compras no aplicativo, ofertas de teste ou interface do usuário que visa a upsell dos usuários para versões pagas ou lojas online para comprar outro conteúdo, aplicativos ou suplementos.

    :::image type="content" source="../../../../assets/images/submission/validation-financial-information-in-app-purchase.png" alt-text="validation-financial-info-in-app-purchase":::

    :::image type="content" source="../../../../assets/images/submission/validation-financial-information-online-stores.png" alt-text="validation-online-store":::

* Se seu aplicativo exigir uma conta, os usuários poderão se inscrever para uma conta sem custo. É proibido o uso do termo **gratuito** ou **conta gratuita**.
* Você pode determinar se uma conta está ativa indefinidamente ou por um tempo limitado. Quando a conta expirar, o aplicativo não deverá mostrar interface do usuário, texto ou links indicando a necessidade de pagamento.
* A política de privacidade e os termos de uso do seu aplicativo devem estar livres de qualquer interface do usuário ou links relacionados ao comércio.

</details>

### <a name="bots"></a>Bots

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.3.2](/legal/marketplace/certification-policies#114032-bots-and-messaging-extension).
<br></br>
<details><summary>Expanda para saber mais</summary>

Para aplicativos que usam o Serviço de Bot do Microsoft Azure (como bots e extensões de mensagens), você deve seguir todos os requisitos definidos na Microsoft [Termos dos Serviços Online](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46).

Os bots sempre devem pedir permissão para fazer upload de um arquivo e exibir uma mensagem de confirmação.

:::image type="content" source="../../../../assets/images/submission/validation-bot-confirmation-message.png" alt-text="validation-bot-confirmation":::

</details>

### <a name="external-domains"></a>Domínios externos

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false"::: Esta seção está alinhada com a [ política do marketplace comercial da Microsoft número1140.3.3 ](/legal/marketplace/certification-policies#114033-external-domains) e fornece orientações ao desenvolvedor sobre o uso de domínios restritos na propriedade do manifesto `validDomains`.
<br></br>
<details><summary>Expanda para saber mais</summary>

Não inclua domínios fora do controle da sua organização (incluindo curingas) e serviços de túnel nas configurações de domínio do aplicativo. As seguintes exceções incluem:

* Se seu aplicativo usar o OAuthCard do Serviço de Bot do Azure, você deverá incluir `token.botframework.com` como um domínio válido ou o botão **Entrar** não funcionará.
* Se seu aplicativo depender do SharePoint, você poderá incluir o site raiz associado do SharePoint como um domínio válido usando a `{teamSiteDomain}` propriedade do contexto.

#### <a name="government-community-cloud-listings"></a>Listas da Nuvem Comunitária Governamental

Para distribuir seu aplicativo para usuários Nuvem da Comunidade Governamental (GCC), o processo de autenticação deve identificar e encaminhar os usuários para uma URL específica ou esperada do GCC, evitando listagens duplicadas no repositório do Teams.

</details>

### <a name="sensitive-content"></a>Conteúdo confidencial

[*Correção Obrigatória*]

Seu aplicativo não deve postar dados confidenciais, como cartão de crédito, detalhes de pagamento financeiro, integridade, rastreamento de contato ou outras informações de identificação pessoal (PII) para um público que não se destina a exibir o conteúdo.

O aplicativo deve avisar os usuários antes de baixar quaisquer arquivos ou executáveis (.exe) no computador ou ambiente do usuário.

## <a name="general-functionality-and-performance"></a>Funcionalidade e desempenho gerais

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4](/legal/marketplace/certification-policies#11404-functionality).

### <a name="launching-external-functionality"></a>Iniciar a funcionalidade externa

[*Correção Obrigatória*]

Os aplicativos não devem tirar os usuários do Teams de cenários de usuários centrais. O conteúdo e as interações do aplicativo devem ocorrer nos recursos do Teams, como bots, Cartões Adaptáveis, guias e módulos de tarefas.
<br></br>
<details><summary>Expanda para saber mais</summary>

Vincule usuários dentro do aplicativo Teams e não a um site ou aplicativo externo. Para cenários que exigem funcionalidade externa, seu aplicativo deve ter permissão explícita do usuário para iniciar a funcionalidade.

O texto do botão da interface do usuário que ativa a funcionalidade externa deve incluir conteúdo para indicar que o usuário foi retirado da instância do Teams. Por exemplo, inclua texto como **Desta forma para Contoso.com** ou **Exibir em Contoso.com**.

</details>

### <a name="compatibility"></a>Compatibilidade

[*Correção Obrigatória*]

Os aplicativos devem estar totalmente funcionais nas versões mais recentes dos seguintes sistemas operacionais e navegadores:

* Microsoft Windows
* macOS
* Microsoft&nbsp;Edge
* Google Chrome
* iOS
* Android

Seu aplicativo deve mostrar uma mensagem de falha normal em navegadores e sistemas operacionais sem suporte.

### <a name="response-time"></a>Tempo de resposta

[*Correção Obrigatória*]

Os aplicativos do Teams devem responder dentro de um período razoável ou mostrar um indicador de carregamento ou digitação ou mensagem ou aviso.

* As guias devem responder dentro de dois segundos ou exibir uma mensagem de carregamento ou aviso.
* Os bots devem responder aos comandos do usuário dentro de dois segundos ou exibir um indicador de digitação.
* As extensões de mensagens devem responder aos comandos do usuário dentro de dois segundos.
* As notificações devem ser exibidas dentro de dois segundos após a ação do usuário.

## <a name="app-package-and-store-listing"></a>Lista do pacote de aplicativos e da loja.

[*Correção Obrigatória*]

Os pacotes de aplicativos devem ser formatados corretamente e incluir todas as informações e componentes necessários.

> [!TIP]  
> Você deve incluir as seguintes instruções de teste detalhadas para validar o envio do aplicativo:
>
> * **Etapas para configurar as contas de teste do aplicativo** caso o aplicativo dependa de contas externas para autenticação.
> * Resumo de **comportamento esperado do aplicativo** para os fluxos de trabalho principais no Teams.
> * **Descreva claramente as limitações**, condições ou exceções à funcionalidade, recursos e resultados na descrição longa do aplicativo e materiais relacionados.
> * **Ênfase em quaisquer considerações** para testadores ao validar o envio do aplicativo.  
> * **Preencher previamente as contas de teste com dados fictícios para auxiliar no teste**.

### <a name="app-manifest"></a>Manifesto do aplicativo

[*Correção Obrigatória*]

O manifesto do aplicativo Teams define a configuração do seu aplicativo.

* Seu manifesto deve estar em conformidade com um esquema de manifesto divulgado publicamente. Para obter mais informações, consulte a [referência do manifesto](~/resources/schema/manifest-schema.md). Não envie seu aplicativo usando uma versão prévia do manifesto.
* Se seu aplicativo incluir um bot ou uma extensão de mensagens, os detalhes no manifesto do aplicativo deverão ser consistentes com os metadados da Estrutura do Bot, incluindo o nome do bot, o logotipo, o link da política de privacidade e o link de termos de serviço.
* Se seu aplicativo usa Azure Active Directory para autenticação, inclua a ID do aplicativo (cliente) do Microsoft Azure Active Directory (Azure AD) no manifesto. Para obter mais informações, consulte a [referência do manifesto](~/resources/schema/manifest-schema.md#webapplicationinfo).

### <a name="app-icons"></a>Ícones do aplicativo

[*Correção Obrigatória*]

Os ícones são um dos principais elementos que as pessoas visualizam ao navegar na loja do Teams. 
<br></br>
<details><summary>Expanda para saber mais</summary>

Seus ícones devem comunicar a marca e a finalidade do aplicativo, aderindo aos seguintes requisitos:

* O pacote do aplicativo deve incluir duas versões .png do ícone do aplicativo: um ícone de cor e um ícone de estrutura de tópicos.
* A versão de cor do ícone deve ter 192 x 192 pixels. O símbolo de ícone pode ser qualquer cor ou cores, mas deve ficar em um plano de fundo quadrado sólido ou totalmente transparente.
* A versão de estrutura de tópicos do ícone é exibida nos seguintes cenários:
  * Quando seu aplicativo está em uso e **hospedado** na barra de aplicativos no lado esquerdo do Teams.
  * Quando um usuário fixa a extensão de mensagens do aplicativo.

* A estrutura de tópicos deve ter 32 x 32 pixels e pode ser branca com uma tela de fundo transparente ou transparente com uma tela de fundo branca. O ícone não deve ter nenhum preenchimento extra ao redor do símbolo.

* O pacote do aplicativo deve incluir ícones formatados e dimensionados corretamente. Os ícones devem corresponder às informações nos metadados de listagem do repositório.

Para obter mais informações, consulte [diretrizes do ícone](~/concepts/build-and-test/apps-package.md#app-icons).

</details>

### <a name="app-descriptions"></a>Descrições do aplicativo

Você deve ter uma descrição curta e longa do seu aplicativo. As descrições nas configurações do seu aplicativo e na Central de parceiros devem ser as mesmas.
<br></br>
<details><summary>Expanda para saber mais</summary>

As descrições não devem ser diretas ou por meio de descrições diferentes de outra marca (de propriedade da Microsoft ou de outra forma). Verifique se sua descrição não inclui declarações que não podem ser fundamentadas. Por exemplo, **Aumento garantido de 200% na eficiência**.

#### <a name="short-description"></a>Descrição breve

Uma breve descrição é um resumo conciso do seu aplicativo que destaca sua proposta de valor e é dirigida ao seu público-alvo.

**O que fazer:**

* Manter a descrição curta em uma frase.
* Colocar primeiro as informações mais importantes.
* Incluir palavras-chave que os clientes provavelmente procurarão.
* Faça uso eficiente do limite de caracteres disponível. Por exemplo, não repita o nome do aplicativo.

**Não fazer:**

[*Correção Sugerida*]

Usar a palavra **aplicativo** na descrição curta.

#### <a name="long-description"></a>Descrição longa

A longa descrição pode fornecer uma narrativa envolvente que destaca a proposta de valor, o público principal e o setor-alvo do seu aplicativo. Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.

**O que fazer:**

* Usar [Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) para formatar sua descrição.
* Usar a voz ativa e falar diretamente com os usuários. Por exemplo, **Você pode...**.
* Listar os recursos com marcadores para que seja mais fácil escanear a descrição.
* Descreva claramente as limitações, os recursos, as condições ou as exceções à funcionalidade e as entregas na listagem e nos materiais relacionados antes que o usuário instale seu aplicativo. As funcionalidades do Teams devem estar relacionadas às funções principais descritas na listagem.
* Certifique-se de que a descrição do aplicativo corresponda à funcionalidade disponível dentro do aplicativo Teams. Qualquer referência a fluxos de trabalho fora do aplicativo Teams deve ser limitada e distintamente chamada a partir da funcionalidade do aplicativo Teams.
* Inclua uma ajuda ou um link de suporte.
* Consulte **Microsoft 365** em vez de **Office 365**.
* Se você precisar referenciar o **Teams**, escreva a primeira referência como **Microsoft Teams**. Referências posteriores podem ser reduzidas para **Teams**.
* Use a seguinte linguagem ao descrever como o aplicativo funciona com o Teams (ou com o Microsoft 365):
  * **... funciona com o Microsoft Teams**.
  * **... trabalhando com o Microsoft Teams.**
  * **... no Microsoft Teams.**
  * **... para o Microsoft Teams.**
  * **... integrado ao Microsoft Teams.**
  * **... criado para...**
  * **... desenvolvido para...**
  * **.. projetado para...**

**O que não fazer:**

[*Correção Obrigatória*]

* Exceder 500 palavras.
* Abreviar **Microsoft** como **MS** ou **MSFT**.
* Indicar que o aplicativo é uma oferta da Microsoft, incluindo o uso de lemas ou linhas de marcação da Microsoft.
* Use nomes de marca protegidos por direitos autorais que você não possui.
* Use o seguinte idioma, a menos que você seja um parceiro certificado da Microsoft:
  * **... certificado para ...**
  * **... da plataforma ...**
* Incluir erros de digitação, erros gramaticais.
* Coloque em maiúsculas desnecessariamente todo o manifesto ou a descrição longa do AppSource ou o conteúdo do aplicativo.
* Incluir links ao AppSource.
* Faça declarações não verificadas. Por exemplo, melhor, superior e classificado, a menos que ele venha com a origem da declaração.
* Compare sua oferta com outras ofertas do marketplace.

</details>

### <a name="screenshots"></a>Capturas de tela

As capturas de tela fornecem uma visualização panorâmica proeminente do seu aplicativo para complementar seu nome, ícone e descrições.
<br></br>
<details><summary>Expanda para saber mais</summary>

Lembre-se do seguinte:

* Você pode ter até cinco capturas de tela por lista.
* Os tipos de arquivo com suporte incluem PNG, JPEG e GIF.
* As dimensões devem ter 1366 x 768 pixels.
* Tamanho máximo de 1.024 KB.

**O que fazer:**

* Concentre-se nos recursos do seu aplicativo. Por exemplo, como as pessoas podem se comunicar com seu bot.
* Incluir conteúdo que represente com precisão seu aplicativo.
* Usar texto de forma criteriosa.
* Capturas de tela de quadro com uma cor que reflete sua marca e inclui conteúdo de marketing.

**O que não fazer:**

[*Correção Sugerida*]

* Mostrar dispositivos específicos, como telefones ou laptops.
* Exibir o Chrome ou a IU que não estiverem no seu aplicativo.
* Capture qualquer Teams ou IU do navegador nas suas capturas de tela.
* Incluir maquetes que reflitam de forma imprecisa a IU real do seu aplicativo, como por exemplo, mostrar seu aplicativo sendo usado fora do Teams.

> [!TIP]  
> Um vídeo pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Um vídeo também é a primeira coisa que os usuários veem na sua listagem. Para obter mais informações, consulte [criar um vídeo para a lista da sua loja](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

</details>

### <a name="privacy-policy"></a>Política de privacidade

[*Correção Obrigatória*]

A política de privacidade pode ser específica para seu aplicativo Teams ou uma política geral para todos os seus serviços.

* Se você usar um modelo de política de privacidade genérico, deverá adicionar uma referência a **serviços**, **aplicativos** ou **plataformas no escopo de sua política de privacidade**. Você não precisa especificar seu aplicativo Teams no escopo, se incluir uma referência a **serviços**, **aplicativos** e **plataformas**. O processo de validação do aplicativo interpretará essas referências para incluir seu aplicativo Teams junto com seus outros serviços ou sites.
* Deve incluir como você lida com o armazenamento, retenção e exclusão de dados do usuário. Você deve descrever os controles de segurança para proteção de dados.
* Deve incluir suas informações de contato.
* Não deve incluir URLs que estão quebradas ou para fins beta ou de preparo.
* Não deve incluir links para AppSource.
* Não deve exigir autenticação para acessar a política de privacidade.
* Não deve incluir nenhuma interface do usuário de comércio ou links da store.

### <a name="terms-of-use"></a>Termos de uso

[*Correção Obrigatória*]

Use as seguintes diretrizes para escrever o Termos de uso:

* Deve ser específico e aplicável à sua oferta.
* Deve ser hospedado em seu próprio domínio.
* Deve ter um link seguro (HTTPS).
* O acesso aos Termos de uso não deve exigir autenticação.

### <a name="support-links"></a>Links de suporte

[*Correção Obrigatória*]

Os URLs de suporte do seu aplicativo não devem exigir autenticação. Por exemplo, os usuários não devem fazer logon para entrar em contato com você.
<br></br>
<details><summary>Expanda para saber mais</summary>

As URLs de suporte devem incluir seus detalhes de contato ou uma maneira de avançar para que os usuários gerem um tíquete de suporte. Por exemplo, se a URL de suporte estiver hospedada no GitHub, a página do GitHub deverá estar sob sua propriedade e deverá incluir os detalhes do contato ou uma maneira de avançar para que os usuários gerem um tíquete de suporte.

:::image type="content" source="../../../../assets/images/submission/validation-supportlinks-authentication.png" alt-text="validation-support-links-auth":::

</details>

### <a name="localization"></a>Localização

[*Correção Obrigatória*]

Se o seu aplicativo oferece suporte à localização, o pacote do aplicativo deve incluir um arquivo com traduções de idiomas que são exibidos com base na configuração de idioma do Teams. O arquivo deve estar em conformidade com o esquema de Localização do Teams. Para obter mais informações, confira [esquema de localização do Teams](~/concepts/build-and-test/apps-localization.md).

## <a name="apps-linked-to-saas-offer"></a>Aplicativos vinculados à oferta de SaaS

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política de mercado comercial da Microsoft número 1140.5](/legal/marketplace/certification-policies?branch=pr-en-us-5673). Se você estiver criando um Teams vinculado a uma oferta de SaaS, verifique se ele segue essas diretrizes.
<br></br>
<details><summary>Geral</summary>

* Os ISVs devem dar suporte à capacidade de vários usuários (Assinantes) no mesmo locatário gerenciarem sua própria assinatura e atribuir licenças aos usuários no locatário.
* A oferta deve atender a todos os [requisitos técnicos](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/include-saas-offer) para aplicativos Teams vinculados a uma oferta SaaS.
* Os aplicativos Teams vinculados à oferta SaaS devem atender a todos os requisitos definidos em [1000 Software as a Service (SaaS)](/legal/marketplace/certification-policies#1000-software-as-a-service-saas).
* `subscriptionOffer` detalhes mencionados no arquivo de manifesto devem estar corretos. No manifesto do seu aplicativo, adicione ou atualize o nó `subscriptionOffer` com valor `publisherId.offerId`. Por exemplo, se seu ID de editor é `contoso1234` e seu ID de oferta é `offer01`, o valor que você especifica no manifesto do aplicativo deve ser `contoso1234.offer01`.
* A oferta de SaaS vinculado ao aplicativo Teams deve estar ativa no AppSource e as ofertas de visualização não são aceitas para aprovação da loja.

</details>

</br>
<details><summary>Metadados da oferta</summary>

* Os metadados da oferta devem corresponder ao manifesto do Teams, à listagem de aplicativos do Teams no AppSource e à oferta de SaaS no AppSource.
* O aplicativo Teams e a oferta de SaaS devem ser do mesmo editor ou desenvolvedor. A oferta de SaaS referenciada no manifesto do aplicativo deve pertencer ao mesmo editor que o aplicativo Teams é enviado ao marketplace comercial.
* Como sua oferta enviada é um aplicativo Teams vinculado à oferta SaaS, você deve selecionar **Compras adicionais** como **Sim, meu produto requer a compra de um serviço ou oferece compras adicionais** no aplicativo na seção de configuração de produtos do Partner Center de sua lista de ofertas.
* As descrições do plano e os detalhes de preços devem fornecer informações suficientes para que os usuários entendam claramente as listagens de ofertas.
* Quaisquer limitações, dependências de serviços adicionais e exceções aos recursos oferecidos devem ser destacadas com precisão nas descrições do plano.
* Os aplicativos do Teams vinculados à oferta de SaaS foram projetados para dar suporte a licenças atribuídas por usuário. Às vezes, a oferta de SaaS é criada com outro método ou tem fluxos de compra especializados. Você deve mencionar claramente nos metadados do aplicativo e nos detalhes do plano de assinatura sobre o método e os fluxos de compra.
* A oferta de SaaS deve fornecer mensagens e diretrizes para todos os usuários em todos os estados aplicáveis do fluxo de compra.

</details>
</br>

<details><summary>Gerenciamento de licenças e home page oferta de SaaS</summary>

* Forneça uma introdução aos assinantes sobre como usar o produto.
* Permitir que o assinante atribua licenças.
* Forneça diferentes maneiras de se envolver com o suporte para problemas, tais como perguntas frequentes, base de dados de conhecimento e endereço de email.
* Valide os usuários para garantir que eles ainda não tenham licença atribuída por meio de outro usuário.
* Notifique os usuários após a atribuição de licença.
* Oriente os usuários pelo chatbot ou email do Teams sobre como adicionar o aplicativo ao Teams e começar.

</details>
</br>

<details><summary>Usabilidade e funcionalidade</summary>

* Após a compra bem-sucedida e atribuição de licenças, você deve fornecer o seguinte:
* Acesso aos usuários para recursos do plano assinado.
* Adição de valor e benefícios significativos do plano de assinatura aos usuários.
* No aplicativo Teams, forneça um link para o aplicativo SaaS home page os assinantes gerenciem as licenças no futuro.

</details>
</br>

<details><summary>Configurar e testar o aplicativo SaaS</summary>

Se a configuração do seu aplicativo para fins de teste for complexa, forneça um documento funcional de ponta a ponta, etapas de configuração de oferta de SaaS vinculado e instruções para gerenciamento de licenças e usuários como parte de suas "Notas para Certificação".

> [!TIP]  
> Você pode adicionar um vídeo sobre como o gerenciamento de aplicativos e licenças funciona para ajudar a equipe a testar.

</details>

## <a name="tabs"></a>Guias

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.2](/legal/marketplace/certification-policies#114042-tabs).
Se seu aplicativo incluir uma guia, verifique se ele segue essas diretrizes.
> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes de design da guia do Teams](~/tabs/design/tabs.md).

</br>
<details><summary>Configurar</summary>

* A configuração da guia **não deve deixar** um novo usuário sem saída. Forneça uma mensagem sobre como concluir a ação ou o fluxo de trabalho. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-create-new-account.png" alt-text="validation-tabs-setup-create-new-acc":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-missing-forward-guidance.png" alt-text="validation-tabs-missing-fwd-guidance":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-new-user.png" alt-text="validation-tabs-set-up-new-user":::

* Para obter a melhor experiência de primeira execução, autentique seus usuários durante a configuração da guia e não depois. A autenticação pode ocorrer fora da janela de configuração da guia. [*Correção Sugerida*]

* O usuário não deve sair da experiência de configuração de guia dentro do Teams para criar conteúdo fora do Teams e, em seguida, retornar ao Teams para fixá-lo. A tela de configuração da guia deve explicar o valor da configuração e como configurá-lo. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-profile-name.png" alt-text="validation-tabs-set-up-profile-name":::

* A tela de configuração da guia não deve inserir um site inteiro. Mantenha sua experiência de configuração focada. Por exemplo, se você estiver criando um aplicativo de gerenciamento de projeto que permite que os usuários configurem um projeto em um canal, mantenha a tela de configuração da guia focada em permitir que o usuário selecione um projeto de seu aplicativo para configurar no canal. [*Correção obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configuration-experience.png" alt-text="validation-tabs-setup-configuration-exp":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configuration-screen.png" alt-text="validation-tabs-set-up-configuration-screen":::

* A tela de configuração da guia não deve solicitar que os usuários insiram uma URL. Pedir aos usuários para configurar uma URL durante a configuração da guia é uma experiência do usuário quebrada, o usuário sai da tela de configuração da guia, adquire a URL, retorna à tela de configuração e insere a URL. Um recurso de equipes preexistente já permite que os usuários fixem um link de site no canal. Se o aplicativo solicitar que o usuário insira uma URL do site durante a configuração da guia e o aplicativo estiver limitado para exibir todo o conteúdo do site na guia do canal, seu aplicativo não oferecerá valor significativo ao usuário. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configured-url.png" alt-text="validation-tabs-set-up-configured-url":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configured-url-two.png" alt-text="validation-tabs-set-up-configured-url-two":::

</details>
</br>

<details><summary>Visualizações</summary>

* A área de tela de entrada não deve usar logotipos grandes. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-applogin.png" alt-text="validation-views-app-login":::

* O conteúdo pode ser simplificado por meio da divisão entre várias guias. [*Correção Sugerida*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-multiple-tabs.png" alt-text="val-views-multiple-tabs":::

* As guias não devem ter um cabeçalho duplicado. Remova o logotipo duplicado do iframe, pois a estrutura de guias já exibe o ícone e o nome do aplicativo. [*Correção sugerida*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-duplicate-header-logo.png" alt-text="validation-views-duplicate-head-logo":::

</details>
</br>

<details><summary>Navegação</summary>

Estas são as diretrizes de navegação:

* As guias não devem fornecer navegação que entre em conflito com a navegação primária do Teams. Se você fornecer uma navegação à esquerda em sua guia, ela não deverá incluir apenas ícones ou ícones com texto empilhado. Não deve ser um corrimão dobrável com a opção de ver ícones com texto empilhado (imitando a barra de navegação Equipes). Inclua ícones com texto embutido ou apenas texto ou use menus de hambúrguer em vez do trilho esquerdo da guia. [*Correção Obrigatória*]

Projete seu aplicativo com componentes da interface do usuário do Fluent [básicos](~/concepts/design/design-teams-app-basic-ui-components.md) e [avançados](~\concepts\design\design-teams-app-advanced-ui-components.md).

:::image type="content" source="../../../../assets/images/submission/validation-navigation-static-tab.png" alt-text="validation-nav-static-tab":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-horizontal-rail.png" alt-text="validation-nav-horizontal-rail":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-left-navigation.png" alt-text="validation-navigation-left-nav":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-icon-text.png" alt-text="validation-nav-icon-text":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-collapsable-left-rail.png" alt-text="validation-nav-collapsable-left-rail":::

* As guias com barra de ferramentas no trilho esquerdo devem deixar o espaçamento de 20px da navegação à esquerda do Teams. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-spacing-between-toolbar.png" alt-text="validation-nav-spacing-between-toolbar":::

* As páginas secundária e terceira em uma guia devem ser abertas em uma exibição de nível dois (L2) e nível três (L3) na área da guia principal, que é navegada por trilhas ou navegação à esquerda. Você também pode incluir os seguintes componentes para auxiliar na navegação por tabulação: [*Correção Obrigatória*]
  * Botões de voltar
  * Cabeçalhos da página
  * Menus de hambúrguer
* A guia não deve ter uma rolagem horizontal. Aplicativos de quadro de comunicações e outros aplicativos que exigem uma tela maior para permitir que os usuários colaborem sem uma experiência de aplicativo desfeita, podem usar a rolagem horizontal dependendo de suas necessidades de negócios. [*Correção sugerida*]

* Links profundos em guias não devem ser vinculados a uma página da Web externa, mas ao Teams. Por exemplo, módulos de tarefa ou outras guias. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-view-button-not-linked-static-tab.png" alt-text="validation-nav-view-button-not-linked-static-tab":::

* As guias não devem permitir que os usuários naveguem para fora do Teams para a experiência principal do aplicativo. As guias podem redirecionar para fora do Teams para fluxos de trabalho não principais. Por exemplo, para gerar um tíquete de suporte. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-core-workflow-within-configuration.png" alt-text="validation-nav-core-workflow-within-configuration":::

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-core-workflow-redirects-outside.png" alt-text="validation-nav-core-workflow-redirects-outside":::

</details>
</br>

<details><summary>Usabilidade</summary>

* As guias devem fornecer valor além de hospedar um site existente. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-usability-app-provides-workflows.png" alt-text="validation-usability-app-provides-work-flows":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-website-i-framed.png" alt-text="validation-usability-website-i-frame":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-teams-app-identical-website.png" alt-text="validation-usability-teams-app-identical-websites":::

* O conteúdo não deve truncar ou sobrepor-se na guia.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-content-truncation.png" alt-text="validation-usability-content-truncations":::

* Os usuários devem poder desfazer sua última ação na guia.

* As guias em um contexto pessoal podem agregar conteúdo de instâncias compartilhadas do aplicativo. Por exemplo, um aplicativo de gerenciamento de projeto com uma guia configurável que permite aos membros do canal comentar sobre o projeto em cartões Kanban, deve agregar esse conteúdo e exibir no aplicativo pessoal. [*Correção Sugerida*]

* As guias devem responder aos temas do Teams. Quando um usuário altera o tema, o tema do aplicativo deve refletir a seleção.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-responsive-tabs.png" alt-text="validation-usability-responsive-tab":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-unresponsive-tabs.png" alt-text="validation-usability-unresponsive-tab":::

* As guias devem usar componentes com estilo do Teams, como fontes do Teams, rampas de tipo, paletas de cores, sistema de grade, movimento, tom de voz e assim por diante, sempre que possível. Para obter mais informações, confira [diretrizes de design de guia](/microsoftteams/platform/tabs/design/tabs). [*Correção sugerida*]

    :::image type="content" source="../../../../assets/images/submission/validation-usability-app-uses-diff-font.png" alt-text="validation-usability-app-uses-font":::

* Se a funcionalidade do aplicativo exigir alterações nas configurações, inclua uma guia **Configurações**. [*Correção Sugerida*]
* As guias devem seguir o design de interação do Teams, como navegação na página, posição e uso de caixas de diálogo, hierarquias de informações e assim por diante. Para obter mais informações, confira [Kit de interface do usuário do Microsoft Teams Fluent](~/concepts/design/design-teams-app-basic-ui-components.md)

* O conteúdo da guia no iframe não deve incluir recursos que imitam os principais recursos do Teams. Por exemplo, bots, extensões de mensagens, chamada, reunião, e assim por diante.

* O conteúdo na página de aterrissagem das guias configuráveis deve ser contextualmente o mesmo para todos os membros do canal.

* O conteúdo na página de aterrissagem de guias configuráveis não deve ter o escopo definido para uso individual e não incluir conteúdo pessoal, como **Minhas Tarefas** ou **Meu Painel**.

* Se seu aplicativo exigir o provisionamento de uma exibição de escopo pessoal para o usuário melhorar a eficiência ou a produtividade do local de trabalho, use exibições filtradas, links profundos para aplicativos pessoais ou navegue até modos de exibição L2 ou L3 dentro da guia configurável e mantenha a página de aterrissagem contextualmente igual para todos os usuários.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-configurable-tab-personal-info.png" alt-text="validation-usability-configurble-tab-pers-info":::

* As guias configuráveis devem ter a funcionalidade focalizada.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-configurable-nested-tabs.png" alt-text="validation-usability-configurble-nested-tab":::

* As experiências de tabulação devem ser totalmente responsivas em dispositivos móveis (Android e iOS).

> [!TIP]
>
> * Inclua um bot pessoal junto com uma guia pessoal.
> * Permitir que os usuários compartilhem o conteúdo da sua guia pessoal.

</details>

## <a name="bots"></a>Bots

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.3](/legal/marketplace/certification-policies#114043-bots).

Se seu aplicativo incluir um bot, verifique se ele segue essas diretrizes.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, confira [Diretrizes de design de bot do Teams](~/bots/design/bots.md).

</br>
<details><summary>Comandos do bot</summary>

É difícil analisar a entrada do usuário e prever a intenção do usuário. Os comandos de bot fornecem aos usuários um conjunto de palavras ou frases para o bot entender.

* A lista de comandos de bot com suporte nas configurações do aplicativo é altamente recomendada. Esses comandos são exibidos na caixa de composição quando um usuário tenta enviar uma mensagem ao bot.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-listed.png" alt-text="validation-bot-commands-list":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-not-listed.png" alt-text="validation-bot-commands-not-list":::

* Todos os comandos compatíveis com o bot devem funcionar corretamente, incluindo comandos genéricos como **Oi**, **Olá** e **Ajuda**.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-help-command.png" alt-text="validation-bots-help-command":::

* Os comandos do bot não devem levar um usuário a um beco sem saída, os comandos devem sempre fornecer um caminho a seguir.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-deadend.png" alt-text="validation-bot-commands-dead-end":::

> [!TIP]
> Quanto aos bots pessoais, inclua uma guia **Ajuda** que descreve ainda mais o que seu bot pode fazer.

</details>
</br>

<details><summary>Mensagens de boas-vindas do bot</summary>

* Se o aplicativo tiver um fluxo de configuração complexo (requer uma licença corporativa ou não tem um fluxo de inscrição intuitivo), os bots nesses aplicativos sempre deverão enviar uma mensagem de boas-vindas durante a primeira execução.

Para obter a melhor experiência, a mensagem de boas-vindas deve incluir o valor oferecido pelo bot aos usuários, que instalaram o bot no canal, como configurar o bot e descrever brevemente todos os comandos de bot com suporte. Você pode exibir a mensagem de boas-vindas usando um Cartão Adaptável com botões para melhorar a usabilidade. Para obter mais informações, consulte [como acionar uma mensagem de boas-vindas do bot](~/bots/how-to/conversations/send-proactive-messages.md). Para aplicativos sem um fluxo de configuração complexo, você pode optar por disparar uma mensagem de boas-vindas durante a experiência de primeira execução do bot. No entanto, se uma mensagem de boas-vindas for disparada, ela deverá seguir as diretrizes da mensagem de boas-vindas.

:::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message.png" alt-text="validation-bot-welcom-message":::

:::image type="content" source="../../../../assets/images/submission/validation-bot-no-welcome-message.png" alt-text="validation-bot-no-wel-come-message":::

* As mensagens de boas-vindas do bot em canais e bate-papos são opcionais durante a primeira execução, especialmente se o bot estiver disponível para uso pessoal e executar ações semelhantes. Seu bot não deve enviar mensagens de boas-vindas aos usuários individualmente (ele é considerado [spam](#botmessagespamming)). A mensagem também deve mencionar a pessoa que adicionou o bot.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message-not-triggered.png" alt-text="validation-bot-welcome-message-not-trigger":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message-triggered.png" alt-text="validation-bot-wel-message-trigger":::

> [!TIP]
> Em mensagens de boas-vindas a usuários individuais, um tour por carrossel pode fornecer uma visão geral eficaz do bot e de qualquer outro recurso de aplicativo para incentivar os usuários a experimentar comandos de bot. Por exemplo, **Criar uma tarefa**.

</details>
</br>

<details><summary><a id="botmessagespamming">Spam de mensagens de bot</a></summary>

Os bots não devem enviar spam aos usuários enviando várias mensagens em curta duração.

* **Mensagens de bot em canais e bate-papos**: não enviar spam aos usuários criando postagens separadas. Crie uma única postagem com respostas na mesma conversa.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-message-spamming-one-message.png" alt-text="validation-bot-message-spam-one-message":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-message-spamming-multiple-messages.png" alt-text="validation-bot-message-spam-multiple-message":::

* **Mensagens de bot em aplicativos pessoais**:
  * Não envie várias mensagens em uma duração rápida.
  * Envie uma mensagem com informações completas.
  * Evite conversas de vários turnos para concluir um único fluxo de trabalho repetitivo.
  * Use um formulário (ou módulo de tarefa) para coletar todas as entradas de um usuário de uma só vez.
  * Chatbots conversacionais baseados em NLP podem usar conversas de vários turnos para tornar a discussão mais envolvente e concluir um fluxo de trabalho.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-using-task-module.png" alt-text="validation-bot-message-using-task-module":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-using-mutliple-conversation.png" alt-text="validation-bot-messages-using-mutliple-conversations":::

* **Mensagens de boas-vindas**: não repita a mesma mensagem de boas-vindas em intervalos regulares. Por exemplo, quando um novo membro é adicionado a uma equipe, não crie spam para outros membros com uma mensagem de boas-vindas. Envie uma mensagem ao novo membro pessoalmente.

</details>
</br>

<details><summary>Notificações de bot</summary>

As notificações de bot devem incluir conteúdo relevante ao escopo definido pelo bot (equipe, bate-papo ou pessoal).

:::image type="content" source="../../../../assets/images/submission/validation-bot-notifications-relevant.png" alt-text="validation-bot-notification-relevant":::

:::image type="content" source="../../../../assets/images/submission/validation-bot-notifications-not-relevant.png" alt-text="validation-bot-notification-not-not-relevant":::

</details>
</br>
<details><summary>Bots e Cartões Adaptáveis</summary>

Os Cartões Adaptáveis são uma forma altamente recomendada de exibir mensagens de bot. Os cartões devem ser leves e incluir apenas até seis ações. Para exibir mais conteúdo, considere o uso de um módulo ou guia de tarefa.

Para obter mais informações sobre cartões, consulte:

* [Design dos Cartões Adaptáveis](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Referência dos cartões](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

A experiência do bot deve ser totalmente responsiva em dispositivos móveis. As respostas do bot devem fornecer uma maneira de avançar quando aplicável. O bot deve ser responsivo e falhar com uma mensagem de erro normal para falhas. As mensagens de bot enviadas no escopo pessoal para a base do usuário em gatilhos em um escopo colaborativo devem fornecer informações contextuais (incluindo a origem ’ da mensagem).

</details>
</br>

<details><summary>Bots somente de notificação</summary>

Aplicativos que consistem em bots somente de notificação fornecem valor ao usuário disparando notificações do usuário com base em determinados gatilhos ou eventos no aplicativo principal ou back-end. Por exemplo, um novo cliente potencial de vendas é adicionado para a equipe de vendas acompanhar. Um bot somente de notificação de alta qualidade notifica os usuários regularmente sobre determinadas conclusões de eventos, como preenchimentos de fluxo de trabalho ou alertas.

Uma notificação fornecerá valor no Teams se:

1. O cartão ou o texto postado fornece detalhes adequados que não exigem mais nenhuma ação do usuário.
1. O cartão ou texto postado fornece informações de visualização adequadas para que um usuário execute uma ação ou decida exibir mais detalhes em um link aberto fora do Teams.

Os aplicativos que fornecem apenas notificações com conteúdo como **Você tem uma nova notificação, clique para exibir** e exigem que o usuário navegue fora do Teams para tudo o mais não fornecem valor significativo dentro do Teams.

:::image type="content" source="../../../../assets/images/submission/validation-navigation-static-tab.png" alt-text="validation-nav-static-tab":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-horizontal-rail.png" alt-text="validation-nav-horizontal-rail":::

:::image type="content" source="../../../../assets/images/submission/validation-bot-notification-only-inadequete-info.png" alt-text="validation-bot-notifications-only-inadequete-info":::

> [!TIP]
> Visualize informações e forneça ações básicas do usuário embutido no cartão postado para que o usuário não seja solicitado a navegar para fora do Teams para todas as ações (independentemente da complexidade).

</details>

## <a name="message-extensions"></a>Extensões de mensagens

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.4](/legal/marketplace/certification-policies#114044-messaging-extensions).

Se seu aplicativo inclui uma extensão de mensagem, certifique-se de que segue essas diretrizes.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes de design de extensão de mensagens do Teams](~/messaging-extensions/design/messaging-extension-design.md).

</br>
<details><summary>Comandos de ação</summary>

As extensões de mensagens baseadas em ação devem fazer o seguinte:

* Permitir que os usuários disparem ações em uma mensagem sem concluir etapas intermediárias, como entrar.

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-no-intermediate-step.png" alt-text="validation-messaging-extension-no-intermediate-steps":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-intermediate-step-available.png" alt-text="validation-messaging-extension-intermediate-steps-available":::

* Transferir o contexto da mensagem ao próximo estado de trabalho. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-app-passes-message.png" alt-text="validation-messaging-extension-app-passes-messages":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-app-doesnot-pass-message.png" alt-text="validation-messaging-extension-app-doesnot-pass-messages":::

* Incorpore o nome do aplicativo host em vez de um verbo genérico para comandos de ação disparados de uma mensagem de chat, postagem de canal ou chamada para ação em aplicativos. Por exemplo, use **Iniciar uma Reunião do Skype** para **Iniciar Reunião**, **Carregar arquivo para DocuSign** para **Carregar arquivo** e assim por diante. [*Correção Sugerida*]

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-action-command-host-name.png" alt-text="validation-messaging-extension-action-command-host-names":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-action-command-verb.png" alt-text="validation-messaging-extension-action-commands-verb":::

</details>
</br>

<details><summary>Links de visualização (desenrolar do link)</summary>

[*Correção Obrigatória*]

As extensões de mensagens devem visualizar links reconhecidos na caixa de redação do Teams. Não adicione domínios que estão fora do seu controle (URLs absolutas ou curingas). Por exemplo, `yourapp.onmicrosoft.com` é válido, `*.onmicrosoft.com` não é válido. Domínios de nível superior também são proibidos. Por exemplo: `*.com` ou `*.org`. [*Correção Obrigatória*]

</details>
</br>

<details><summary>Comandos de pesquisa</summary>

* Extensões de mensagens baseadas em pesquisa devem fornecer texto que ajude os usuários a pesquisar com eficiência. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-search-commands-text-available.png" alt-text="validation-search-command-text-available":::

* @menções executáveis devem ser claras, fáceis de entender, e acessíveis.

    :::image type="content" source="../../../../assets/images/submission/validation-search-command-unclear-executable.png" alt-text="validation-search-commands-unclear-executable":::

</details>
</br>

<details><summary>Comandos de ação</summary>Aplicativos de extensão de mensagens baseados em pesquisa

[*Correção Obrigatória*]

Os aplicativos que consistem na extensão de mensagens baseada em pesquisa fornecem valor ao usuário compartilhando cartões que permitem conversas contextuais sem alternância de contexto.

Para passar na validação de um aplicativo somente de extensão de mensagem baseado em pesquisa, os itens a seguir são necessários como linha de base para garantir que a experiência do usuário não seja interrompida. Um cartão compartilhado por meio de uma extensão de mensagens fornecerá valor no Teams se:

1. O cartão postado fornece detalhes adequados que não exigem mais nenhuma ação do usuário.
1. O cartão postado fornece informações de visualização adequadas para um usuário executar uma ação ou decidir exibir mais detalhes em um link que abre fora do Teams.

    :::image type="content" source="../../../../assets/images/submission/validation-search-based-messaging-ext-adequete-info.png" alt-text="validation-search-base-messaging-ext-adequete-info":::

    :::image type="content" source="../../../../assets/images/submission/validation-search-based-messaging-ext-inadequete-info.png" alt-text="validation-search-base-messaging-ext-inadequete-info":::

Os aplicativos de desbloqueio de links não fornecem um valor significativo para as equipes. Considere a criação de fluxos de trabalho adicionais em seu aplicativo, se seu aplicativo só oferece suporte para o desenrolamento de link e não tem nenhuma outra funcionalidade.

</details>

## <a name="task-modules"></a>Módulos de tarefas

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.5](/legal/marketplace/certification-policies#114045-task-modules).
<br></br>
<details><summary>Expanda para saber mais</summary>

Um módulo de tarefa deve incluir um ícone e o nome curto do aplicativo ao qual está associado. Os módulos de tarefas não devem incorporar um aplicativo inteiro e apenas exibir os componentes necessários para concluir uma ação específica.

Para obter mais informações, confira [Diretrizes de design do módulo de tarefas do Teams](~\task-modules-and-cards\task-modules\design-teams-task-modules.md).

:::image type="content" source="../../../../assets/images/submission/validation-task-module-displays-components.png" alt-text="validation-task-module-displays-component":::

:::image type="content" source="../../../../assets/images/submission/validation-task-module-embeds-app.png" alt-text="validation-task-module-embed-app":::

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, confira [Diretrizes de design do módulo de tarefas do Teams](~/task-modules-and-cards/task-modules/design-teams-task-modules.md).

</details>

## <a name="meeting-extensions"></a>Extensões de reunião

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.6](/legal/marketplace/certification-policies#114046-meeting-extensions).
> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, confira as [diretrizes de design de extensão de reunião do Teams](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

</br>
<details><summary>Geral</summary>

Use as seguintes diretrizes para extensões de reunião:

* Os aplicativos de extensibilidade de reunião devem oferecer uma experiência de reunião responsiva e alinhada à experiência de reunião do Teams. A experiência na reunião é obrigatória, as experiências pré e pós-reunião não são obrigatórias.

  * Com a experiência de aplicativo de pré-reunião, os usuários podem encontrar e adicionar aplicativos de reunião. Os usuários também podem executar tarefas de pré-reunião, como desenvolver uma votação para pesquisar os participantes da reunião. Se seu aplicativo fornecer uma experiência de pré-reunião, ele deverá ser relevante para o fluxo de trabalho da reunião.

  * Com a experiência do aplicativo pós-reunião, os usuários podem exibir os resultados da reunião, como resultados da pesquisa de pesquisa ou comentários, bem como outros conteúdos do aplicativo. Se seu aplicativo fornecer uma experiência pós-reunião, ele deverá ser relevante para o fluxo de trabalho da reunião.

  * Com a experiência do aplicativo na reunião, você pode envolver os participantes da reunião durante a reunião e aprimorar a experiência de reunião para todos os participantes. Os participantes não devem ser retirados da reunião do Teams para concluir os principais fluxos de trabalho do usuário do seu aplicativo.

* Seu aplicativo deve oferecer valor além de fornecer cenas personalizadas do Modo Conferência no Teams.

* O recurso de estágio de reunião compartilhada só pode ser iniciado por meio do aplicativo da área de trabalho do Teams. No entanto, a experiência de consumo do estágio de reunião compartilhada deve ser utilizável e não interrompida quando exibida em dispositivos móveis.

> [!TIP]
> Você deve declarar `groupchat` como um escopo em `configurableTabs` e `meetingDetailsTab`, ou `meetingChatTab` e `meetingSidePanel` como uma propriedade de contexto no manifesto para habilitar seu aplicativo para reuniões no Teams mobile.

</details>

</br>
<details><summary>Experiência de pré e pós-reunião</summary>

* As telas de pré e pós-reunião devem seguir as diretrizes gerais de design de guia. Para obter mais informações, confira [diretrizes de design do Teams](~/tabs/design/tabs.md).
* As guias não devem conter rolagem horizontal.
* As guias devem ter um layout organizado ao exibir vários itens. Por exemplo, mais de 10 enquetes ou pesquisas, veja o [layout de exemplo](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Seu aplicativo deve notificar os usuários quando os resultados de uma pesquisa ou votação são exportados, declarando **Resultados baixados com êxito**.

</details>

</br>
<details><summary>Experiência na reunião</summary>

* Os aplicativos só devem usar um tema escuro durante as reuniões. Para obter mais informações, confira [diretrizes de design do Teams](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming).
* Uma dica de ferramenta deve exibir o nome do aplicativo ao passar o mouse sobre o ícone do aplicativo durante as reuniões.

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-display-app-name.png" alt-text="validation-in-meeting-exp-display-app-names":::

* As extensões de mensagens devem funcionar da mesma forma durante as reuniões, assim como fora delas.

</details>

</br>
<details><summary>Guias na reunião</summary>

* Deve responder.
* Deve manter o preenchimento e os tamanhos dos componentes.
* Deve ter um botão Voltar se houver mais de uma camada de navegação.

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-back-button.png" alt-text="validation-in-meeting-exp-back-buttons":::

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-back-button-absent.png" alt-text="validation-in-meeting-exp-back-buttons-absent":::

* Não deve incluir mais de um botão fechar. Isso pode confundir os usuários, pois já existe um botão de cabeçalho interno para ignorar a guia.
* Não deve conter rolagem horizontal.

</details>

</br>
<details><summary>Caixas de diálogo na reunião</summary>

* Deve ser usado com moderação e para cenários que são leves e orientados a tarefas.
* Deve exibir o conteúdo em uma única coluna e não possuir vários níveis de navegação.
* Não deve usar módulos de tarefa.
* Deve alinhar-se ao centro do estágio da reunião.

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-dialog-not-aligned.png" alt-text="validation-in-meeting-dialog-not-align":::

* Deve ser ignorado depois que um usuário seleciona um botão ou executa uma ação.

* **Modo Conferência**: considere as seguintes práticas recomendadas para uma experiência de criação de cena:
  * Todas as imagens estão no formato .png.
  * O pacote final com todas as imagens juntas não deve exceder a resolução 1920x1080. A resolução é um número par. Essa resolução é um requisito para que as cenas sejam mostradas com êxito.
  * O tamanho máximo da cena é de 10 MB.
  * O tamanho máximo de cada imagem é de 5 MB. Uma cena é uma coleção de várias imagens. O limite é para cada imagem individual.
  * Selecione **Transparente** conforme necessário. Essa caixa de seleção está disponível no painel direito quando uma imagem é selecionada. As imagens sobrepostas devem ser marcadas como Transparentes para indicar que estão sobrepondo imagens na cena.

</details>

## <a name="notifications"></a>Notificações

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.7](/legal/marketplace/certification-policies#114047-notification-apis).

Se o seu aplicativo usa as APIs de feed de [atividades fornecidas pelo Microsoft Graph](/graph/teams-send-activityfeednotifications), certifique-se de seguir as seguintes diretrizes.
<br></br>
<details><summary>Geral</summary>

* Todos os gatilhos de notificação especificados na configuração do aplicativo devem funcionar.
* As notificações devem ser localizadas de acordo com os idiomas suportados configurados no seu aplicativo.
* As notificações devem ser exibidas em cinco segundos a partir da ação do usuário.

</details>
</br>
<details><summary>Avatares</summary>

* O avatar de notificação deve corresponder ao ícone de cor do aplicativo.
* As notificações disparadas por um usuário devem incluir o avatar do usuário.

</details>
</br>
<details><summary>Spam</summary>

* Os aplicativos não devem enviar mais de 10 notificações por minuto para um usuário.
* Os bots e o feed de atividades não devem disparar notificações duplicadas.
* As notificações devem fornecer valor aos usuários e não devem ser usadas em eventos triviais ou irrelevantes.

</details>
</br>
<details><summary>Navegação e layout</summary>

* As notificações devem aderir ao layout e à experiência do feed de atividades do Teams.
* Ao selecionar uma notificação, o usuário deve ser direcionado ao conteúdo relevante no Teams.

</details>

## <a name="microsoft-365-app-compliance-program"></a>Programa de Conformidade do Aplicativo do Microsoft 365

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.6](/legal/marketplace/certification-policies#11406-publisher-attestation).
<br></br>
<details><summary>Expanda para saber mais</summary>

O Programa de Conformidade dos Aplicativos do Microsoft 365 tem como objetivo ajudar as organizações a avaliarem e gerenciarem riscos através da avaliação de informações de segurança e conformidade do seu aplicativo. Se você publicar um aplicativo na loja do Teams, precisará concluir os seguintes níveis do programa:

* **Verificação do Editor**: ajuda os administradores e usuários finais a entenderem a autenticidade dos desenvolvedores de aplicativos que se integram à plataforma de identidade da Microsoft. Quando concluído, um selo azul **verificado** é exibido na caixa de diálogo de consentimento Azure Active Directory e em outras telas. Para obter mais informações, consulte [Marcar seu aplicativo como verificado pelo editor](/azure/active-directory/develop/mark-app-as-publisher-verified).

    :::image type="content" source="../../../../assets/images/submission/validation-365-compliance-publisher-verification.png" alt-text="validation-365-compliance-publisher-verifications":::

* **Atestado do Editor**: um processo no qual você compartilha informações gerais, de tratamento de dados, e de segurança e conformidade para ajudar os clientes em potencial a tomarem decisões informadas sobre como usar seu aplicativo.

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false"::: Se você estiver enviando um aplicativo que não foi listado anteriormente, não poderá concluir oficialmente o Atestado de Editor até que seu aplicativo esteja na loja do Teams. Se você atualizar um aplicativo listado, conclua o Atestado do Editor antes de enviar a versão mais recente do aplicativo.

</details>

## <a name="advertising"></a>Publicidade

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png" border="false":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.7](/legal/marketplace/certification-policies#11407-advertising).

Os aplicativos não devem exibir anúncios, incluindo anúncios dinâmicos, anúncios em faixa e anúncios na mensagem.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma conta do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)

## <a name="see-also"></a>Confira também

* [Distribuir seu aplicativo](~/concepts/deploy-and-publish/apps-publish-overview.md)
* [Preparar o envio para a Microsoft Store](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [Testar e depurar seu aplicativo](~/concepts/build-and-test/debug.md)
* [Criar uma conta de desenvolvedor do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
