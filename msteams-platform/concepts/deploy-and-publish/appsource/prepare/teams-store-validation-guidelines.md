---
title: Diretrizes de validação da loja do Microsoft Teams
description: Saiba como aumentar as chances de seu aplicativo passar no processo de envio da loja do Microsoft Teams. Entenda as correções obrigatórias e sugeridas. Explore as diretrizes de validação.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: 0a0151c72820baf1b6bd39ee00539cacbd3fa38b
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560759"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Diretrizes de validação da loja do Microsoft Teams

Seguir essas diretrizes aumenta as chances de seu aplicativo ser aprovado no processo de envio à store do Microsoft Teams. As diretrizes específicas do Teams complementam as [políticas de certificação do marketplace comercial](/legal/marketplace/certification-policies#1140-teams) da Microsoft e são atualizadas com frequência para refletir novos recursos, comentários do usuário e alterações nas regras de negócios.

> [!NOTE]
>
> * É possível que algumas diretrizes não sejam pertinentes ao seu aplicativo. Por exemplo, se seu aplicativo não incluir um bot, você poderá ignorar as diretrizes relacionadas ao bot.
> * Cruzamos essas diretrizes com as políticas de certificação comercial da Microsoft e adicionamos o que fazer e o que não fazer com exemplos de cenários de aprovação ou reprovação encontrados em nosso processo de validação.
> * Determinadas diretrizes são marcadas como *Correção Obrigatória*. Se o envio do aplicativo não atender a essas diretrizes obrigatórias, você receberá um relatório de falha conosco com etapas para atenuar. O envio do aplicativo passará na Validação da loja do Microsoft Teams somente depois que você corrigir os problemas.
> * Other guidelines are marked as *Suggested Fix*. For an ideal user experience, we suggest that you fix the issues, however, your app submission will not be blocked from publishing on the Teams store, if you choose not to fix the issues.

:::row:::
   :::column:::
      :::image type="icon" source="../../../../assets/icons/value-proposition.png" link="#value-proposition" border="false":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../../assets/icons/security.png" link="#security" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/function.png" link="#general-functionality-and-performance" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/package.png" link="#app-package-and-store-listing" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/saas-offer.PNG" link="#apps-linked-to-saas-offer" border="false":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/tab.png" link="#tabs" border="false":::
   :::column-end:::
   :::column:::
      :::image type="icon" source="../../../../assets/icons/bot.png" link="#bots-1" border="false":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../../assets/icons/messaging-extension.png" link="#message-extensions" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/task-module.png" link="#task-modules" border="false":::
   :::column-end:::
     :::column span="":::
      :::image type="icon" source="../../../../assets/icons/meeting.png" link="#meeting-extensions" border="false":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/notifications.png" link="#notifications" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/microsoft-365.png" link="#microsoft-365-app-compliance-program" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/advertising.png" link="#advertising" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/crypto-currency-based-apps-icon.png" link="#cryptocurrency-based-apps" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/app-functionality-icon.png" link="#app-functionality" border="false":::
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/mobile-experience-icon.png" link="#mobile-experience" border="false":::
   :::column-end:::
:::row-end:::

## <a name="value-proposition"></a>Proposta de valor

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png"::: Esta seção está alinhada com a [Política de certificação comercial da Microsoft número 1140.1](/legal/marketplace/certification-policies#11401-value-proposition-and-offer-requirements) e fornece orientações adicionais aos desenvolvedores de aplicativos do Microsoft Teams sobre a proposta de valor das suas ofertas.

### <a name="app-name"></a>Nome do aplicativo

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png"::: Esta seção está alinhada com a [ política de certificação comercial da Microsoft número 1140.1.1 ](/legal/marketplace/certification-policies#114011-app-name) e fornece orientações adicionais aos desenvolvedores sobre como nomear seus aplicativos.
<br></br>
<details><summary>Expanda para saber mais</summary>

O nome de um aplicativo desempenha um papel fundamental na forma como os usuários o descobrem na loja. Use as seguintes diretrizes para nomear um aplicativo:

* O nome deve incluir termos relevantes aos seus usuários.
* Prefixo ou sufixo substantivos comuns com o nome do desenvolvedor. Por exemplo, **Tarefas da Contoso** em vez de **Tarefas**.
* Não deve usar o **Teams** ou outros nomes de produtos da Microsoft, como Excel, PowerPoint, Word, OneDrive, SharePoint, OneNote, Azure, Surface e Xbox, que podem indicar falsamente a co-identidade visual ou a venda conjunta. Para obter mais informações sobre como fazer referência a produtos e serviços de software da Microsoft, confira [Marca Registrada e Diretrizes da Marca Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
* Não é preciso copiar o nome de um aplicativo listado na loja ou em outra oferta no mercado comercial.
* Não deve conter termos profanos ou depreciativos. O nome também não deve incluir linguagem racial ou culturalmente insensível.
* Deve ser exclusivo. Se seu aplicativo (Contoso) estiver listado na loja do Microsoft Teams e no Microsoft AppSource e você quiser listar outro aplicativo específico para uma geografia, como Contoso México, seu envio deverá atender aos seguintes critérios:
  * Chame a funcionalidade específica da região do aplicativo no título, metadados, experiência do aplicativo de primeira resposta e seções de ajuda. Por exemplo, o título deve ser Contoso México. O título do aplicativo deve diferenciar claramente um aplicativo existente do mesmo desenvolvedor para evitar confusão para o usuário final.
  * Ao fazer o upload do pacote do aplicativo no Partner Center, selecione os **Mercados** certos onde o aplicativo estará disponível na seção **Disponibilidade**.

* O nome do aplicativo não deve liderar com um recurso principal do Teams, como Chat, Contatos, Calendário, Chamadas, Arquivos, Atividade, Teams, Aplicativos e Ajuda. O nome do aplicativo pode ser reduzido para Chat, Contatos, Calendário, Chamadas, Arquivos, Atividade, Equipes, Aplicativos e Ajuda na instalação no painel de navegação esquerdo.

* If your app is part of an official partnership with Microsoft, the name of your app must come first. For example, **Contoso Connector for Microsoft Teams**.

* O nome do aplicativo não deve ter nenhuma referência aos produtos da Microsoft ou da Microsoft. Não use o **Teams**, **a Microsoft** ou **o Aplicativo** no nome do aplicativo, a menos que seu aplicativo esteja em parceria oficial com a Microsoft. Nesse caso, o nome do aplicativo deve vir primeiro antes de qualquer referência à Microsoft. Por exemplo, o **conector da Contoso para o Microsoft Teams**.

* Não use parênteses na nomenclatura para incluir produtos da Microsoft.

* O nome do desenvolvedor deve ser o mesmo no manifesto e no AppSource.

* Os manifestos de aplicativo enviados devem ser manifestos de produção. Da mesma forma, o nome do aplicativo não deve indicar que o aplicativo é um aplicativo de pré-produção. Por exemplo, o nome do aplicativo não deve conter palavras como Beta, Desenvolvimento, Versão Prévia e UAT.

 > [!TIP]
 > A identidade visual do aplicativo na loja do Microsoft Teams e no AppSource, incluindo o nome do aplicativo, o nome do desenvolvedor, o ícone do aplicativo, as capturas de tela do AppSource, o vídeo, a breve descrição e o site, separadamente ou em conjunto, não devem representar uma oferta oficial da Microsoft, a menos que seu aplicativo seja uma oferta oficial do Microsoft 1P.

</details>

### <a name="suitable-for-workplace-consumption"></a>Adequado para o consumo no local de trabalho

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png"::: Esta seção está alinhada com a política de certificação comercial da Microsoft número [1140.1.2](/legal/marketplace/certification-policies#114012-workplace-appropriateness), [100.8](/legal/marketplace/certification-policies#1008-significant-value), e [100.10](/legal/marketplace/certification-policies#10010-inappropriate-content) e fornece orientações adicionais aos desenvolvedores sobre como criar aplicativos apropriados para o local de trabalho.
<br></br>
<details><summary>Expanda para saber mais</summary>

O conteúdo do aplicativo deve ser adequado para consumo geral no local de trabalho e seguir todas as restrições listadas nas políticas de certificação do mercado comercial. É proibido o conteúdo relacionado à religião, política, jogos de azar e entretenimento prolongado.

Seu aplicativo deve permitir a colaboração em grupo, melhorar a produtividade de um indivíduo ou ambos. Os aplicativos destinados à união e socialização da equipe devem ser colaborativos e projetados para vários participantes. Os aplicativos não devem exigir um investimento de tempo substancial de mais de 60 minutos por sessão ou afetar a produtividade.

</details>

### <a name="similar-platforms-and-services"></a>Plataformas e serviços semelhantes

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política de certificação comercial da Microsoft número 1140.1.3](/legal/marketplace/certification-policies#114013-other-platforms-and-services).

Os aplicativos devem se concentrar na experiência do Teams e não incluir nomes, ícones ou imagens de outras plataformas ou serviços de colaboração baseados em chat semelhantes no conteúdo do aplicativo ou nos metadados do aplicativo, a menos que o aplicativo forneça interoperabilidade específica.

### <a name="feature-names"></a>Nomes de recursos

Os nomes de recursos do aplicativo em botões e outros textos da interface do usuário não devem usar a terminologia reservada para o Teams e outros produtos da Microsoft. Por exemplo, **Iniciar reunião**, **Fazer chamada** ou **Iniciar chat** são nomes de recursos em uso pela Microsoft no Microsoft Teams. Se necessário, inclua o nome do aplicativo para tornar a distinção clara, como **Iniciar reunião da Contoso**.

### <a name="authentication"></a>Autenticação

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png"::: Esta seção está alinhada com a [política de certificação comercial da Microsoft número1140.1.4 ](/legal/marketplace/certification-policies#114014-access-to-services) e fornece orientações aos desenvolvedores sobre como autenticar seus aplicativos com serviços externos.

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
  
* **Experiências de compartilhamento de conteúdo**: os aplicativos que requerem autenticação com um serviço externo para compartilhar conteúdo nos canais do Teams devem indicar claramente na documentação de ajuda (ou recursos semelhantes) como desconectar ou cancelar o compartilhamento de conteúdo se esse recurso for compatível com o serviço externo. Isso não significa que a capacidade de cancelar o compartilhamento de conteúdo deve estar presente no seu aplicativo do Teams.

</details>

## <a name="security"></a>Segurança

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política de certificação comercial da Microsoft número 1140.3](/legal/marketplace/certification-policies#11403-security).

### <a name="financial-information"></a>Informações financeiras

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png"::: Esta seção está embutida com o número [1140.3.1](/legal/marketplace/certification-policies#114031-financial-transactions) da política de certificação comercial da Microsoft e fornece diretrizes sobre a transmissão de informações financeiras na interface do Teams e notifica os desenvolvedores sobre cenários de pagamento restritos na versão móvel (Android e iOS) do aplicativo Teams.
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
* You can determine whether an account is active indefinitely or for a limited time. When the account expires the app must not show UI, text, or links indicating the need to pay.
* A política de privacidade e os termos de uso do seu aplicativo devem estar livres de qualquer interface do usuário ou links relacionados ao comércio.

</details>

### <a name="bots"></a>Bots

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.3.2](/legal/marketplace/certification-policies#114032-bots-and-messaging-extension).
<br></br>
<details><summary>Expanda para saber mais</summary>

Para aplicativos que usam o Serviço de Bot do Microsoft Azure (como bots e extensões de mensagens), você deve seguir todos os requisitos definidos na Microsoft [Termos dos Serviços Online](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46).

Os bots sempre devem pedir permissão para fazer upload de um arquivo e exibir uma mensagem de confirmação.

:::image type="content" source="../../../../assets/images/submission/validation-bot-confirmation-message.png" alt-text="validation-bot-confirmation":::

</details>

### <a name="external-domains"></a>Domínios externos

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png"::: Esta seção está alinhada com a [ política do marketplace comercial da Microsoft número1140.3.3 ](/legal/marketplace/certification-policies#114033-external-domains) e fornece orientações ao desenvolvedor sobre o uso de domínios restritos na propriedade do manifesto `validDomains`.
<br></br>
<details><summary>Expanda para saber mais</summary>

Don't include domains outside of your organization's control (including wildcards) and tunneling services in your app's domain configurations. The following exceptions include:

* Se seu aplicativo usar o OAuthCard do Serviço de Bot do Azure, você deverá incluir `token.botframework.com` como um domínio válido ou o botão **Entrar** não funcionará.
* Se seu aplicativo depender do SharePoint, você poderá incluir o site raiz associado do SharePoint como um domínio válido usando a `{teamSiteDomain}` propriedade do contexto.
* Não use domínios de nível superior, como **.com**, **.in** e **.org** como um domínio válido. [*Correção Obrigatória*]

* Não use **o .onmicrosoft.com ou** como um domínio válido em que **a onmicrosoft** não está sob seu controle. No entanto, você pode **yoursite.com** como um domínio válido em que seu **site** está sob seu controle, mesmo que o domínio inclua um curinga. [*Correção Obrigatória*]

* Se seu aplicativo for um PowerApp criado no Microsoft Power Platform, você deverá incluir apps.powerapps.com  como um domínio válido para permitir que seu aplicativo seja acessível e funcional no Teams.

</details>

### <a name="sensitive-content"></a>Conteúdo confidencial

[*Correção Obrigatória*]

Seu aplicativo não deve postar dados confidenciais, como cartão de crédito, detalhes de pagamento financeiro, integridade, rastreamento de contato ou outras informações de identificação pessoal (PII) para um público que não se destina a exibir o conteúdo.

O aplicativo deve avisar os usuários antes de baixar quaisquer arquivos ou executáveis (.exe) no computador ou ambiente do usuário.

## <a name="general-functionality-and-performance"></a>Funcionalidade e desempenho gerais

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4](/legal/marketplace/certification-policies#11404-functionality).

* As diretrizes de avanço são obrigatórias para usuários administradores e existentes. Você pode adicionar diretrizes de avanço como hiperlinks para se inscrever, começar, entrar em contato conosco, links de ajuda ou email.
* Chamar a dependência ou as limitações da conta na funcionalidade do aplicativo não é necessário, mas é obrigatório adicioná-la na descrição longa do manifesto e na listagem de aplicativos do AppSource.
* Você deve chamar qualquer dependência de administradores de locatário para novos usuários. Se não houver nenhuma dependência, é obrigatório fornecer uma inscrição, entrar em contato conosco, um link de introdução ou um email.

### <a name="launching-external-functionality"></a>Iniciar a funcionalidade externa

[*Correção Obrigatória*]

Os aplicativos não devem tirar os usuários do Teams de cenários de usuários centrais. O conteúdo e as interações do aplicativo devem ocorrer nos recursos do Teams, como bots, Cartões Adaptáveis, guias e módulos de tarefas.
<br>
</br>

<details><summary>Expanda para saber mais</summary>

* Vincule usuários dentro do aplicativo Teams e não a um site ou aplicativo externo. Para cenários que exigem funcionalidade externa, seu aplicativo deve ter permissão explícita do usuário para iniciar a funcionalidade.

* O texto do botão da interface do usuário que ativa a funcionalidade externa deve incluir conteúdo para indicar que o usuário foi retirado da instância do Teams. Por exemplo, inclua texto como **Desta forma para Contoso.com** ou **Exibir em Contoso.com**.

* Adicione **o ícone pop-out** para permitir que os usuários saibam que eles estão sendo navegados fora do Teams. Você pode usar o ícone pop-out :::image type="icon" source="../../../../assets/icons/pop-out-icon.png" ::: à direita do link.

* Se não for possível adicionar um **ícone pop-out** , você poderá implementar qualquer uma das seguintes opções para informar ao usuário que ele está sendo navegado para fora do Teams:
  * Adicione uma observação no Cartão Adaptável informando que, quando os usuários selecionam **Obter** Ajuda usando este aplicativo, ele leva o usuário para fora do Teams.
  * Adicionar diálogos intersticiais.

</details>

### <a name="compatibility"></a>Compatibilidade

[*Correção Obrigatória*]

Os aplicativos devem estar totalmente funcionais nas versões mais recentes dos seguintes sistemas operacionais e navegadores:

* Microsoft Windows
* macOS
* Microsoft Edge
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
>
> * Você deve garantir que as contas de teste fornecidas ou o ambiente de teste seja válido em perpetuidade, ou seja, até que o aplicativo esteja ativo no marketplace comercial.
> * Você deve incluir as seguintes instruções de teste detalhadas para validar o envio do aplicativo:
>
>   * **Etapas para configurar as contas de teste do aplicativo** caso o aplicativo dependa de contas externas para autenticação.
>   * Resumo de **comportamento esperado do aplicativo** para os fluxos de trabalho principais no Teams.
>   * **Descreva claramente as limitações**, condições ou exceções à funcionalidade, recursos e resultados na descrição longa do aplicativo e materiais relacionados.
>   * **Ênfase em quaisquer considerações** para testadores ao validar o envio do aplicativo.
>   * **Preencher previamente as contas de teste com dados fictícios para auxiliar no teste**.
>   * Se você estiver fornecendo suas contas de teste, certifique-se de habilitar a integração de terceiros. Além disso, desabilite a autenticação multifator ou de dois fatores.

### <a name="app-manifest"></a>Manifesto do aplicativo

[*Correção Obrigatória*]

O manifesto do aplicativo Teams define a configuração do seu aplicativo.

* Seu manifesto deve estar em conformidade com um esquema de manifesto divulgado publicamente. Para obter mais informações, consulte a [referência do manifesto](~/resources/schema/manifest-schema.md). Não envie seu aplicativo usando uma versão prévia do manifesto.
* Se seu aplicativo incluir um bot ou uma extensão de mensagens, os detalhes no manifesto do aplicativo deverão ser consistentes com os metadados da Estrutura do Bot, incluindo o nome do bot, o logotipo, o link da política de privacidade e o link de termos de serviço.
* Se seu aplicativo usa Azure Active Directory para autenticação, inclua a ID do aplicativo (cliente) do Microsoft Azure Active Directory (Azure AD) no manifesto. Para obter mais informações, consulte a [referência do manifesto](~/resources/schema/manifest-schema.md#webapplicationinfo).

### <a name="uses-of-latest-manifest-schema"></a>Usos do esquema de manifesto mais recente

* Se o aplicativo usar o SSO (logon único), você deverá declarar Microsoft Azure Active Directory (Azure AD) no manifesto para autenticação do usuário. [*Correção Obrigatória*]

* Você deve usar um esquema de manifesto lançado publicamente. Você pode atualizar o pacote do aplicativo para usar uma versão pública do esquema de manifesto 1.10 ou posterior. [*Correção Obrigatória*]

* Ao enviar uma atualização de aplicativo, aumente apenas o número de versão do aplicativo. A ID do aplicativo atualizado deve corresponder à ID do aplicativo publicado. [*Correção Obrigatória*]

* A presença de arquivos adicionais dentro do pacote do aplicativo não é aceitável. [*Correção Obrigatória*]

* O número de versão deve ser o mesmo no esquema do arquivo de manifesto e no esquema de manifesto de idiomas adicionais. [*Correção Obrigatória*]

* Você deve usar o esquema de manifesto do Teams versão 1.5 ou posterior para localizar seu aplicativo. Para usar o esquema de aplicativo versão 1.5 ou posterior no arquivo manifest.json, `$schema` atualize o atributo para 1.5 ou posterior. Atualize `manifestVersion` a propriedade para `$schema` a versão (1.5 nesse caso). [*Correção Obrigatória*]

* Ao adicionar, atualizar ou remover uma funcionalidade existente, adicionar ou remover manifesto ou metadados do Partner Center, você deve aumentar o número de versão do aplicativo e enviar o novo manifesto do aplicativo em sua conta do Partner Center para validação.

* A cadeia de caracteres de versão deve seguir o padrão SEMVer (SemVer) (Especificação de Controle de Versão Semântico). MENOR. PATCH). [*Correção Obrigatória*]

* Se seu aplicativo exigir que os administradores revisem permissões e concedam consentimento no Centro de administração do Teams, você deverá declarar `webapplicationinfo` no manifesto. Se `webapplicationinfo` não for declarada no manifesto, a página Permissões do  seu aplicativo no Centro de administração do Teams será mostrada como **...** [*Correção obrigatória*]

* Como parte da certificação de aplicativos do Teams, você deve enviar uma versão de produção do manifesto do aplicativo. [*Correção Obrigatória*]

* Recomendamos que você declare a ID do MPN (Microsoft Partner Network) no manifesto. A ID do MPN ajuda a identificar a organização parceira que compila o aplicativo. [*Correção Sugerida*]

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

Você deve ter uma descrição curta e longa para seu aplicativo. As descrições na configuração do aplicativo e no Partner Center devem ser as mesmas.

:::image type="content" source="../../../../assets/images/submission/validation-app-description-adequete-information.png" alt-text="O gráfico mostra um exemplo de descrição de aplicativo adequada no aplicativo Teams.":::

:::image type="content" source="../../../../assets/images/submission/validation-app-description-inadequete.png" alt-text="O gráfico mostra um cenário com falha para uma descrição inadequada do aplicativo.":::

<br></br>
<details><summary>Expanda para saber mais</summary>

As descrições não devem ser diretas ou por meio de descrições diferentes de outra marca (de propriedade da Microsoft ou de outra forma). Verifique se sua descrição não inclui declarações que não podem ser fundamentadas. Por exemplo, **Aumento garantido de 200% na eficiência**.

* A descrição do aplicativo não deve conter informações de marketing comparativos. Por exemplo, não use logotipos ou marcas comerciais concorrentes na listagem de ofertas, incluindo marcas ou outros metadados que fazem referência a ofertas ou marketplaces concorrentes. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-comparitive-marketing-fail.png" alt-text="O gráfico mostra um exemplo de informações de marketing comparativos na descrição do aplicativo.":::

* Detalhes do contato do hiperlink, introdução, ajuda ou inscrição na descrição do aplicativo.

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-contact-deatils-hyperlinked.png" alt-text="O gráfico mostra um exemplo de detalhes de contato hiperlinks nas descrições do aplicativo.":::

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-contact-deatils-not-hyperlinked.png" alt-text="O gráfico mostra um exemplo de detalhes de contato não hiperlinks nas descrições do aplicativo.":::

* A descrição do aplicativo deve identificar o público-alvo desejado, explicar breve e claramente seu valor exclusivo e distinto, identificar produtos da Microsoft e outros softwares com suporte e incluir quaisquer pré-requisitos ou requisitos para seu uso. Você deve descrever claramente quaisquer limitações, condições ou exceções à funcionalidade, aos recursos e às entregas, conforme descrito na listagem e nos materiais relacionados antes que o cliente adquira sua oferta. Os recursos declarados devem estar relacionados às funções principais e à descrição da sua oferta. [*Correção Obrigatória*]

* Se você atualizar o nome do aplicativo, substitua o nome do aplicativo antigo pelo novo nome do aplicativo nos metadados da oferta no manifesto, no AppSource e sempre que aplicável. [*Correção Obrigatória*]

* As limitações e as dependências de conta devem ser destacadas na Descrição do Aplicativo de manifesto, no AppSource e no Partner Center. Por exemplo:
  * Conta corporativa
  * Assinatura paga
  * Outra licença ou conta
  * Idioma
  * Discagem PSTN (Rede Telefônica Pública Comunada)
  * Dependência regional
  * Tempo de entrega para tradutores de reserva ou agentes dinâmicos
  * Funcionalidade baseada em função
  * Dependência no aplicativo nativo

  :::image type="content" source="../../../../assets/images/submission/validation-app-description-limitations-calledout-pass.png" alt-text="O gráfico mostra um exemplo de limitações destacadas na descrição do aplicativo.":::
  
  :::image type="content" source="../../../../assets/images/submission/validation-app-description-limitations-not-calledout-fail.png" alt-text="O gráfico mostra um exemplo de limitações não destacadas nas descrições do aplicativo.":::

* Se o aplicativo tiver suporte para regiões específicas ou localizações geográficas, você deverá chamar essa dependência de região específica na descrição do aplicativo no manifesto, no Partner Center e no AppSource para essa oferta.

* Se você precisar referenciar o Teams, escreva a primeira referência na listagem de aplicativos como Microsoft Teams. Referências posteriores podem ser reduzidas para Teams.

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-teams-reference-pass.png" alt-text="O gráfico mostra um exemplo de referência correta ao Teams na descrição do aplicativo.":::

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-teams-reference-fail.png" alt-text="O gráfico mostra um exemplo de referência incorreta ao Teams na descrição do aplicativo.":::

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

* Verifique se a descrição do aplicativo corresponde à funcionalidade disponível dentro do aplicativo Teams. Qualquer referência a fluxos de trabalho fora do aplicativo Teams deve ser limitada e distintamente chamada a partir da funcionalidade do aplicativo Teams.

* Inclua uma ajuda ou um link de suporte.

* Consulte **Microsoft 365** em vez de **Office 365**.

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

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-microsoft-abbreviated.png" alt-text="O gráfico mostra um exemplo de abreviação da Microsoft como MS ou MSFT pela primeira vez na descrição do aplicativo.":::

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-microsoft-not-abbreviated.png" alt-text="O gráfico mostra um exemplo de não abreviar a Microsoft como MS ou MSFT pela primeira vez na descrição do aplicativo.":::

* Indicar que o aplicativo é uma oferta da Microsoft, incluindo o uso de lemas ou linhas de marcação da Microsoft.

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-offering-from-microsoft.png" alt-text="O gráfico mostra um exemplo de como não indicar a oferta da Microsoft na descrição do aplicativo.":::

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-no-offering-indication-from-microsoft.png" alt-text="Gráfico que mostra um exemplo de como escrever a descrição do aplicativo sem usar slogans e marcas da Microsoft.":::

* Use o seguinte idioma, a menos que você seja um parceiro certificado da Microsoft:
  * **... certificado para ...**
  * **... da plataforma ...**
* Incluir erros de digitação, erros gramaticais.
* Coloque em maiúsculas desnecessariamente todo o manifesto ou a descrição longa do AppSource ou o conteúdo do aplicativo.

   :::image type="content" source="../../../../assets/images/submission/validation-long-description-typos-pass.png" alt-text="O gráfico mostra um exemplo de descrição longa do aplicativo sem erros.":::

   :::image type="content" source="../../../../assets/images/submission/validation-long-description-typos-fail.png" alt-text="O gráfico mostra um exemplo de descrição longa do aplicativo com erros de digitação e erros.":::

* Incluir links ao AppSource.

  :::image type="content" source="../../../../assets/images/submission/validation-app-description-link-to-appsource.png" alt-text="O gráfico mostra um exemplo de um cenário de falha com links para AppSource na descrição longa do aplicativo.":::

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

* Focus on your app's capabilities. For example, how people can communicate with your bot.
* Incluir conteúdo que represente com precisão seu aplicativo.
* Usar texto de forma criteriosa.
* Capturas de tela de quadro com uma cor que reflete sua marca e inclui conteúdo de marketing.
* Use capturas de tela de alta resolução que sejam afiadas e contenham texto legível e claramente legível. [*Correção Obrigatória*]
* Use simulações que descrevem com precisão a interface do usuário real do aplicativo para o benefício dos usuários finais. [*Correção Obrigatória*]
* Forneça pelo menos três capturas de tela na listagem do marketplace do seu aplicativo.
* Se o aplicativo Teams for extensível para outros hubs do Microsoft 365, as capturas de tela fornecidas deverão representar a funcionalidade do aplicativo em outros hubs do Microsoft 365.
* Pelo menos uma captura de tela deve descrever a funcionalidade do aplicativo em dispositivos móveis.
* Recomendamos que você forneça legendas em suas capturas de tela para permitir que o usuário entenda claramente a funcionalidade do aplicativo.

**O que não fazer:**

* Inclua simulações que refletem imprecisamente a interface do usuário real do seu aplicativo, como mostrar seu aplicativo sendo usado fora do Teams.

> [!TIP]
>
> * Um vídeo pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Um vídeo também é a primeira coisa que os usuários veem na sua listagem.
> * Se você optar por fornecer um vídeo na listagem do aplicativo, deverá desativar anúncios nas configurações do YouTube ou vimeo antes de enviar o link de vídeo no Partner Center. Os vídeos fornecidos na listagem de aplicativos não devem ter mais de 90 segundos de duração e devem representar apenas a funcionalidade e a integração do aplicativo com o Microsoft Teams. Para obter mais informações, consulte [criar um vídeo para a lista da sua loja](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

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

* Se o seu aplicativo oferece suporte à localização, o pacote do aplicativo deve incluir um arquivo com traduções de idiomas que são exibidos com base na configuração de idioma do Teams. O arquivo deve estar em conformidade com o esquema de Localização do Teams. Para obter mais informações, confira [esquema de localização do Teams](~/concepts/build-and-test/apps-localization.md).

* O conteúdo dos metadados do aplicativo deve ser o mesmo em `en-us` outros idiomas de localização. [*Correção Obrigatória*]

* Os idiomas com suporte devem ser exibidos na descrição do aplicativo AppSource. Por exemplo, este aplicativo está disponível em X (X= idioma localizado). [*Correção Obrigatória*]

* Se as configurações do cliente do usuário não corresponderem a nenhum dos seus idiomas adicionais, o idioma padrão será usado como o idioma de fallback final. Atualize `localizationInfo` a propriedade com o idioma padrão correto ao qual seu aplicativo dá suporte. [*Correção Obrigatória*]

* Atualize a `localizationInfo` propriedade com o idioma padrão correto ao qual seu aplicativo dá suporte ou adicione conteúdo localizado para manifesto e descrição longa e curta do Partner Center. [*Correção Obrigatória*]

## <a name="apps-linked-to-saas-offer"></a>Aplicativos vinculados à oferta de SaaS

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política de mercado comercial da Microsoft número 1140.5](/legal/marketplace/certification-policies?branch=pr-en-us-5673). Se você estiver criando um aplicativo do Teams vinculado a uma oferta de SaaS, verifique se ele segue essas diretrizes.
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
* Forneça diferentes maneiras de interagir com o suporte para problemas, como perguntas frequentes, base de dados de conhecimento e email.
* Valide os usuários para garantir que eles ainda não tenham licença atribuída por meio de outro usuário.
* Notifique os usuários após a atribuição de licença.
* Orientar os usuários sobre como adicionar o aplicativo ao Teams e começar a usar o chatbot ou email do Teams.

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

Se a configuração do aplicativo para fins de teste for complexa, forneça um documento funcional de ponta a ponta, etapas de configuração da oferta de SaaS vinculada e instruções para gerenciamento de licença e de usuário como parte de suas Notas para Certificação *.*

> [!TIP]
> Você pode adicionar um vídeo sobre como o gerenciamento de aplicativos e licenças funciona para ajudar a equipe a testar.

</details>

## <a name="tabs"></a>Guias

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.2](/legal/marketplace/certification-policies#114042-tabs).
Se seu aplicativo incluir uma guia, verifique se ele segue essas diretrizes.
> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes de design da guia do Teams](~/tabs/design/tabs.md).

</br>
<details><summary>Configurar</summary>

* A configuração da guia **não deve deixar** um novo usuário sem saída. Forneça uma mensagem sobre como concluir a ação ou o fluxo de trabalho. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-new-user.png" alt-text="O gráfico mostra um exemplo de Tab com um dead-end na instalação.":::

* O usuário não deve deixar a experiência de configuração de guia dentro do Teams para criar conteúdo fora do Teams e, em seguida, retornar ao Teams para fixá-lo. A tela de configuração da guia deve explicar o valor da configuração e como configurá-lo. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-profile-name.png" alt-text="validation-tabs-set-up-profile-name":::

* Tab configuration screen must not embed an entire website. Keep your configuration experience focused. For example, if you're building a project management app that lets users configure a project in a channel, keep the tab configuration screen focused on allowing the user to select a project from your app to configure in the channel. [*Mandatory Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configuration-experience.png" alt-text="validation-tabs-setup-configuration-exp":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configuration-screen.png" alt-text="validation-tabs-set-up-configuration-screen":::

* Os aplicativos que exigem que os usuários insiram uma URL durante a configuração de uma guia devem:
  * Forneça uma orientação de encaminhamento adequada para o usuário adquirir ou gerar a URL. [*Correção Obrigatória*]
  * Verifique a URL relevante ou apropriada para a funcionalidade do aplicativo de acordo com a descrição do aplicativo. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-tab-configuration-way-forward-url-pass.png" alt-text="A captura de tela mostra um exemplo de configuração de guia com um caminho para o usuário gerar uma URL.":::
  
    :::image type="content" source="../../../../assets/images/submission/validation-tab-configuration-way-forward-url-fail.png" alt-text="A captura de tela mostra um exemplo de configuração de guia sem um caminho para o usuário gerar uma URL.":::

* Hiperlink entre em contato conosco na tela de configuração em vez de texto sem formatação para ajudar os usuários a entrar em contato com você para obter os requisitos de suporte. [*Correção Obrigatória*]

* Para uma experiência de usuário de primeira execução perfeita, recomendamos que você hiperlink sua URL de suporte ou email na tela de configuração. [*Correção Sugerida*]

</details>
</br>

<details><summary>Visualizações</summary>

* The sign in screen area must not use large logos. [*Mandatory Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-applogin.png" alt-text="validation-views-app-login":::

* O conteúdo pode ser simplificado por meio da divisão entre várias guias.

    :::image type="content" source="../../../../assets/images/submission/validation-views-multiple-tabs.png" alt-text="val-views-multiple-tabs":::

* As guias não devem ter um cabeçalho duplicado. Remova logotipos duplicados do quadro I, pois a estrutura de tabulação já exibe o ícone e o nome do aplicativo. [*Correção Sugerida*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-no-duplicate-header-logo.png" alt-text="O gráfico mostra um exemplo de uma guia sem cabeçalhos e logotipos duplicados.":::

    :::image type="content" source="../../../../assets/images/submission/validation-views-duplicate-header-logo.png" alt-text="O gráfico mostra um exemplo de uma guia com cabeçalhos e logotipos duplicados.":::

</details>
</br>

<details><summary>Navegação</summary>

Estas são as diretrizes de navegação:

* As guias não devem fornecer navegação que entre em conflito com a navegação primária do Teams. Se você fornecer uma navegação à esquerda em sua guia, ela não deverá incluir apenas ícones ou ícones com texto empilhado. Não deve ser um corrimão dobrável com a opção de ver ícones com texto empilhado (imitando a barra de navegação Equipes). Inclua ícones com texto embutido ou apenas texto ou use menus de hambúrguer em vez do trilho esquerdo da guia. [*Correção Obrigatória*]

Projete seu aplicativo com componentes da interface do usuário do Fluent [básicos](~/concepts/design/design-teams-app-basic-ui-components.md) e [avançados](~\concepts\design\design-teams-app-advanced-ui-components.md).

:::image type="content" source="../../../../assets/images/submission/validation-navigation-static-tab.png" alt-text="O gráfico mostra um exemplo de navegação em uma guia que não entra em conflito com a navegação principal do Teams.":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-left-navigation.png" alt-text="O gráfico mostra um exemplo de trilho de navegação à esquerda que entra em conflito com a navegação principal do Teams.":::

* As guias com a barra de ferramentas no trilho esquerdo devem deixar um espaçamento de 20 pixels da navegação à esquerda do Teams. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-spacing-between-toolbar.png" alt-text="validation-nav-spacing-between-toolbar":::

* As páginas secundárias e terciárias em uma guia devem ser abertas em uma exibição de nível dois (L2) e nível três (L3) na área da guia principal, que é navegada por meio de trilhas ou navegação à esquerda. Você também pode usar os seguintes componentes para auxiliar a navegação em uma guia:
  * Botões de voltar
  * Cabeçalhos da página
  * Menus de hambúrguer

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-improper-navigation-leveles.png" alt-text="Captura de tela que mostra um exemplo de caixa de diálogo na reunião com vários níveis de navegação.":::

* Links profundos em guias não devem vincular a uma página da Web externa, mas dentro Teams. Por exemplo, módulos de tarefas ou outras guias. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-view-button-not-linked-static-tab.png" alt-text="validation-nav-view-button-not-linked-static-tab":::

* As guias não devem permitir que os usuários naveguem para fora do Teams para a experiência principal do aplicativo. As guias podem redirecionar para fora do Teams para fluxos de trabalho não principais. Por exemplo, para gerar um tíquete de suporte. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-core-workflow-within-configuration.png" alt-text="validation-nav-core-workflow-within-configuration":::

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-core-workflow-redirects-outside.png" alt-text="validation-nav-core-workflow-redirects-outside":::

* A rolagem horizontal não deve estar presente em uma guia na reunião. [*Correção obrigatória*]

* As caixas de diálogo na reunião usadas em seu aplicativo não devem permitir a rolagem horizontal. Use caixas de diálogo na reunião com moderação e para cenários que são leves e orientados a tarefas. Você pode especificar a largura do quadro I da caixa de diálogo na reunião dentro do intervalo de tamanhos com suporte para levar em conta cenários diferentes. [*Correção Obrigatória*]
* Os módulos de tarefa usados em seu aplicativo não devem permitir a rolagem horizontal. Os módulos de tarefa permitem que você selecione tamanhos diferentes para tornar o conteúdo responsivo sem a necessidade de rolagem horizontal. Se necessário, você pode usar um Modo de Exibição de Estágio (um componente de interface do usuário de tela inteira para exibir o conteúdo da Web) para concluir o fluxo de trabalho sem rolagem horizontal. [*Correção Obrigatória*]

* A rolagem horizontal presente na guia em um chat pessoal, canal e guia de detalhes na reunião em qualquer escopo não será permitida se a tela inteira da guia for rolável, a menos que sua guia use uma tela infinita com elementos de interface do usuário fixos. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-allowed-scenarios.png" alt-text="O gráfico mostra exemplos de todos os cenários em dispositivos móveis em que a rolagem horizontal é permitida.":::

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-allowed-kanban.png" alt-text="O gráfico mostra um exemplo de rolagem horizontal na placa Kanban.":::

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-list-view-components.png" alt-text="O gráfico mostra um exemplo de exibição de lista com muitos componentes.":::

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-fixed-board.png" alt-text="O gráfico mostra um exemplo de rolagem horizontal em uma placa branca com tela infinita e placa fixa.":::

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-in-list-view.png" alt-text="O gráfico mostra um exemplo de rolagem horizontal no modo de exibição de lista.":::

* A rolagem horizontal nos Cartões Adaptáveis não deve estar presente no Teams. [*Correção Obrigatória*]

* O trilho inferior usado para navegação em guias não deve entrar em conflito com a navegação de aplicativo móvel nativo do Teams. [*Correção Obrigatória*]

  :::image type="content" source="../../../../assets/images/submission/validation-tab-bottom-rail-conflicts-with-teams-mobile.png" alt-text="O gráfico mostra um exemplo de uma guia que entra em conflito com a navegação de aplicativo móvel nativo do Teams.":::

</details>
</br>

<details><summary>Usabilidade</summary>

* As guias devem fornecer valor além de hospedar um site existente. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-usability-app-provides-workflows.png" alt-text="O gráfico mostra um exemplo de um aplicativo com um fluxo de trabalho valioso para os membros do canal dentro de uma equipe.":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-website-i-framed.png" alt-text="O gráfico mostra um exemplo de um aplicativo com site inteiro em um quadro de I sem nenhuma opção de voltar.":::

* O conteúdo não deve truncar ou sobrepor-se na guia.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-content-truncation.png" alt-text="validation-usability-content-truncations":::

* Os usuários devem poder desfazer sua última ação na guia.

* As guias em um contexto pessoal podem agregar conteúdo de instâncias compartilhadas do aplicativo. Por exemplo, um aplicativo de gerenciamento de projeto com uma guia configurável que permite aos membros do canal comentar sobre o projeto em cartões Kanban, deve agregar esse conteúdo e exibir no aplicativo pessoal. [*Correção Sugerida*]

* As guias devem responder aos temas do Teams. Quando um usuário altera o tema, o tema do aplicativo deve refletir a seleção.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-responsive-tabs.png" alt-text="O gráfico mostra um exemplo de uma guia que responde a um tema no Teams.":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-unresponsive-tabs.png" alt-text="O gráfico mostra um exemplo de uma guia que não responde ao tema no Teams.":::

* As guias devem usar componentes com estilo do Teams, como fontes do Teams, rampas de tipos, paletas de cores, sistema de grade, movimento, tom de voz, sempre que possível. Para obter mais informações, confira [diretrizes de design de guia](/microsoftteams/platform/tabs/design/tabs). [*Correção Sugerida*]

    :::image type="content" source="../../../../assets/images/submission/validation-usability-app-uses-diff-font.png" alt-text="A captura de tela mostra um exemplo de uma guia com fonte calibri em vez da fonte nativa do Teams.":::

* Se a funcionalidade do aplicativo exigir alterações nas configurações, inclua uma guia **Configurações**. [*Correção Sugerida*]
* As guias devem seguir o design de interação do Teams, como navegação na página, posição e uso de caixas de diálogo, hierarquias de informações. Para obter mais informações, consulte [o kit de interface do usuário do Microsoft Teams Fluent](~/concepts/design/design-teams-app-basic-ui-components.md).

* As experiências de tabulação devem ser totalmente responsivas em dispositivos móveis (Android e iOS).

   > [!TIP]
   >
   > * Inclua um bot pessoal junto com uma guia pessoal.
   > * Permitir que os usuários compartilhem o conteúdo da sua guia pessoal.

* Tab não deve conter elementos que obstruam completamente ou impedem fluxos de trabalho dentro da guia. Por exemplo, o bot dentro de uma guia que não pode ser minimizada.

   :::image type="content" source="../../../../assets/images/submission/validation-tab-elements-impede-workflow.png" alt-text="O gráfico mostra um exemplo de guia com elementos que impedem fluxos de trabalho dentro da guia.":::

* Tab não deve ter uma funcionalidade quebrada. Sua oferta deve ser uma solução de software utilizável e deve fornecer a funcionalidade, os recursos e os produtos, conforme descrito em sua listagem e outros materiais relacionados. [*Correção Obrigatória*]

* Se as guias contiverem um rodapé, remova todos os links não relacionados à funcionalidade do aplicativo do rodapé.

</details>
</br>

<details><summary>Seleção de escopo</summary>

* O conteúdo na página de aterrissagem de guias configuráveis não deve ter o escopo definido para uso individual e não incluir conteúdo pessoal, como **Minhas Tarefas** ou **Meu Painel**.

   :::image type="content" source="../../../../assets/images/submission/validation-configurable-tab-content-personal-scope.png" alt-text="O gráfico mostra um exemplo de conteúdo em uma guia configurável com escopo pessoal, como Minhas tarefas ou Meu painel.":::

* Após a experiência de configuração, a página de aterrissagem deve mostrar uma exibição colaborativa para toda a equipe.

* Se seu aplicativo exigir o provisionamento de uma exibição de escopo pessoal para o usuário melhorar a eficiência ou a produtividade do local de trabalho, use exibições filtradas, links profundos para aplicativos pessoais ou navegue até modos de exibição L2 ou L3 dentro da guia configurável e mantenha a página de aterrissagem contextualmente igual para todos os usuários.

* O conteúdo na página de aterrissagem das guias configuráveis deve ser contextualmente o mesmo para todos os membros do canal.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-configurable-tab-personal-info.png" alt-text="O gráfico mostra um exemplo de conteúdo na página de aterrissagem das guias configuráveis contextualmente diferentes para todos os membros.":::

* As guias configuráveis devem ter a funcionalidade focalizada.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-configurable-nested-tabs.png" alt-text="validation-usability-configurble-nested-tab":::

</details>
<br/>

## <a name="bots"></a>Bots

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.3](/legal/marketplace/certification-policies#114043-bots).

Se seu aplicativo incluir um bot, verifique se ele segue essas diretrizes.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, confira [Diretrizes de design de bot do Teams](~/bots/design/bots.md).

</br>
<details><summary>Diretrizes de design de bot</summary>

* Seu aplicativo Teams deve seguir as [diretrizes de design de bot do Teams](../../../../bots/design/bots.md).

* Você deve implementar um módulo de tarefa para evitar a resposta de bot de vários turnos quando o fluxo de trabalho envolve o usuário executando tarefas repetitivas. Por exemplo, use um módulo de tarefa para capturar repetidamente o nome, o dob, o local e a designação em vez de usar conversas de vários turnos. [*Correção Obrigatória*]

* Quaisquer links, respostas ou fluxos de trabalho desfeitos em seu aplicativo devem ser corrigidos. [*Correção Obrigatória*]

</details>

</br>
<details><summary>Comandos do bot</summary>

Analyzing user input and predicting user intent is difficult. Bot commands provide users a set of words or phrases for your bot to understand.

* Você deve listar pelo menos um comando de bot com suporte na seção `{commandList}` do manifesto do aplicativo. Esses comandos são exibidos na caixa de composição quando um usuário tenta enviar uma mensagem ao bot.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-listed.png" alt-text="O gráfico mostra um exemplo de comandos de bot listados no manifesto do aplicativo.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-not-listed.png" alt-text="O gráfico mostra um exemplo de comandos de bot não listados no manifesto do aplicativo.":::

* Todos os comandos compatíveis com o bot devem funcionar corretamente, incluindo comandos genéricos como **Oi**, **Olá** e **Ajuda**.
  
  :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-generic-response-pass.png" alt-text="O gráfico mostra um exemplo de bot respondendo a comandos genéricos.":::

  :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-generic-no-response.png" alt-text="O gráfico mostra um exemplo de bot sem resposta a comandos genéricos.":::

* Os comandos do bot não devem levar um usuário a um beco sem saída, os comandos devem sempre fornecer um caminho a seguir.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-deadend.png" alt-text="validation-bot-commands-dead-end":::

* Você deve listar pelo menos um comando de bot `items.commands.title` válido na seção do manifesto e adicionar uma descrição adequada que dê clareza ao usuário sobre o comando do bot e seu uso. Comandos de bot listados `commandLists` na seção da superfície de manifesto como comandos preenchidos previamente no menu de comando do bot e fornecem um caminho para o novo usuário interagir com o bot. [*Correção Obrigatória*]

* A resposta do bot não deve conter nenhuma imagem oficial do produto da Microsoft ou avatares. Use seus próprios ativos em seu aplicativo. O uso de imagens de produto da Microsoft em seu aplicativo não é permitido. Você só poderá copiar, modificar, distribuir, exibir, licenciar ou vender imagens de produto com direitos autorais da Microsoft se receber permissão explícita dentro do CONTRATO de Licença do End-User (EULA), termos de licença que acompanham o conteúdo ou nas diretrizes de Marca e Marca da [Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks). [*Correção Obrigatória*]

* Os bots devem responder aos comandos do usuário sem exibir um indicador de carregamento contínuo. [*Correção Obrigatória*]

* A resposta do comando de ajuda do bot não deve redirecionar o usuário para fora do Teams. A resposta do comando de ajuda do bot pode redirecionar o usuário para uma tela dentro do aplicativo Teams ou fornecer uma resposta de avanço em um Cartão Adaptável. [*Correção Obrigatória*]

  :::image type="content" source="../../../../assets/images/submission/validation-bot-redirects-user-outside-teams.png" alt-text="O gráfico mostra um exemplo de resposta do bot redirecionando o usuário para fora do Teams.":::

* Os bots sempre devem fornecer uma resposta válida para uma entrada do usuário, mesmo que a entrada seja irrelevante ou inadequada. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-response-valid-improper-input.png" alt-text="O gráfico mostra um exemplo de uma resposta válida para o comando de bot inadequado.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-response-improper-response-invalid-command.png" alt-text="O gráfico mostra um exemplo de uma resposta inválida para o comando de bot inadequado.":::

* Caracteres especiais, como barra (**/**), não devem ser prefixados para comandos de bot. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-special-characters.png" alt-text="O gráfico mostra um exemplo de um cenário com falha em que caracteres especiais são prefixados para comandos de bot.":::

* Os bots devem fornecer uma resposta válida a comandos de usuário inválidos. Os bots não devem encerrar o usuário ou exibir um erro se um usuário enviar um comando de bot inválido. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-way-forward-for-invalid-command.png" alt-text="O gráfico mostra um exemplo de bot fornecendo uma maneira de avançar para um comando inválido.":::

   :::image type="content" source="../../../../assets/images/submission/validation-welcome-message-bot-dead-end-invalid-command.png" alt-text="O gráfico mostra um exemplo de um cenário com falha em que um bot envia uma mesma resposta para um comando válido e inválido.":::

* A funcionalidade do bot deve ser relevante para o escopo no qual o bot está instalado e o bot deve fornecer valor no escopo instalado. [*Correção Obrigatória*]

* Os bots não devem conter comandos duplicados. [*Correção Obrigatória*]

* Os bots não devem exibir um indicador de digitação depois de responder ao comando do usuário, mas podem exibir um indicador de digitação ao responder ao comando do usuário. [*Correção Obrigatória*]

* Os bots devem fornecer uma resposta válida ao  comando de ajuda digitado em letras minúsculas ou maiúsculas que forneçam ao usuário um caminho adiante ou que permita que o usuário acesse o conteúdo da ajuda relacionado ao uso do bot. Os bots devem fornecer uma resposta válida mesmo quando o usuário não tiver feito logon no aplicativo. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-valid-response-lowercase.png" alt-text="O gráfico mostra um exemplo de bot que não fornece uma resposta válida para um comando em letras minúsculas ou maiúsculas.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-valid-response-logged-app.png" alt-text="O gráfico mostra um exemplo de um bot sem uma resposta válida quando o usuário não fez logon no aplicativo.":::

* Os bots devem fornecer uma resposta válida para o **comando de** ajuda.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-help-command.png" alt-text="O gráfico mostra um exemplo de bot enviando uma resposta válida para o comando de ajuda.":::

* As respostas do bot no dispositivo móvel devem ser responsivas sem qualquer truncamento de dados que dificulta o uso do bot do usuário final para concluir os fluxos de trabalho desejados. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-response-no-truncate-mobile.png" alt-text="O gráfico mostra um exemplo de uma mensagem de bot sem truncar no celular.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-response-truncate-mobile.png" alt-text="O gráfico mostra um exemplo de uma mensagem de bot truncando no celular.":::

* Todos os links em um cartão adaptável de resposta do bot devem ser responsivos. Qualquer link que leva o usuário para fora da plataforma do Teams deve ter um texto de redirecionamento claro, como, **Exibir em..** ou **Dessa forma, um** ícone pop-out no botão de ação de resposta do bot ou ter um texto de redirecionamento adequado no corpo da mensagem de resposta do bot. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-action-button-redirect-warning.png" alt-text="O gráfico mostra um exemplo do botão de ação de resposta do bot com um redirecionamento.":::

* Por design, se o bot não responder ou dar suporte a nenhum comando de usuário e for um bot unidirecional destinado apenas a notificar os usuários. Você deve definir `isNotificationOnly` como true no manifesto. [*Correção Obrigatória*]

  :::image type="content" source="../../../../assets/images/submission/validation-bot-command-isnotification-only-true.png" alt-text="O gráfico mostra um exemplo de propriedade somente de notificação definida como true no manifesto do aplicativo.":::

  :::image type="content" source="../../../../assets/images/submission/validation-bot-command-isnotification-only-not-true.png" alt-text="O gráfico mostra um exemplo de notificação apenas que o bot não está respondendo para a mensagem de um usuário.":::

* A experiência do usuário do bot não deve ser interrompida em plataformas móveis. Seu bot deve estar totalmente responsivo no celular. [*Correção Obrigatória*]

> [!TIP]
> Quanto aos bots pessoais, inclua uma guia **Ajuda** que descreve ainda mais o que seu bot pode fazer.

</details>
</br>

<details><summary>Mensagens de boas-vindas do bot</summary>

* Se o aplicativo tiver um fluxo de configuração complexo (requer uma licença corporativa ou não tem um fluxo de inscrição intuitivo), os bots nesses aplicativos sempre deverão enviar uma mensagem de boas-vindas durante a primeira execução.

  Para obter a melhor experiência, a mensagem de boas-vindas deve incluir o valor oferecido pelo bot aos usuários, que instalaram o bot no canal, como configurar o bot e descrever brevemente todos os comandos de bot com suporte. Você pode exibir a mensagem de boas-vindas usando um Cartão Adaptável com botões para melhorar a usabilidade. Para obter mais informações, consulte [como acionar uma mensagem de boas-vindas do bot](~/bots/how-to/conversations/send-proactive-messages.md). Para aplicativos sem um fluxo de configuração complexo, você pode optar por disparar uma mensagem de boas-vindas durante a experiência de primeira execução do bot. No entanto, se uma mensagem de boas-vindas for disparada, ela deverá seguir as diretrizes da mensagem de boas-vindas.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message.png" alt-text="O gráfico mostra um exemplo de bot enviando uma mensagem de boas-vindas quando o bot tem um fluxo de trabalho de configuração complexo.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-no-welcome-message.png" alt-text="O gráfico mostra um exemplo de bot que não envia uma mensagem de boas-vindas quando o bot tem um fluxo de trabalho de configuração complexo.":::

* As mensagens de boas-vindas do bot em canais e bate-papos são opcionais durante a primeira execução, especialmente se o bot estiver disponível para uso pessoal e executar ações semelhantes. Seu bot não deve enviar mensagens de boas-vindas aos usuários individualmente (ele é considerado [spam](#botmessagespamming)). A mensagem também deve mencionar a pessoa que adicionou o bot.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message-not-triggered.png" alt-text="validation-bot-welcome-message-not-trigger":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message-triggered.png" alt-text="validation-bot-wel-message-trigger":::

* Somente bots de notificação devem enviar uma mensagem de boas-vindas que esclarece que o bot é apenas um bot de notificação e os usuários não poderão interagir com o bot. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-notification-only-welcome-message-pass.png" alt-text="O gráfico mostra um exemplo de bot enviando uma mensagem de boas-vindas de que ele é apenas um bot de notificação.":::

* A mensagem de boas-vindas não deve encerrar o usuário. A mensagem de boas-vindas deve incluir o valor oferecido pelo bot aos usuários que instalaram o bot no canal, como configurar o bot e descrever brevemente todos os comandos de bot com suporte. Você pode exibir a mensagem de boas-vindas usando um Cartão Adaptável com botões para melhorar a usabilidade. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-welcome-message-no-way-forward.png" alt-text="O gráfico mostra um exemplo de um cenário com falha em que o bot não tem como avançar para o usuário em uma mensagem de boas-vindas.":::

   :::image type="content" source="../../../../assets/images/submission/validation-welcome-message-clear-way-forward.png" alt-text="O gráfico mostra um exemplo de mensagem de boas-vindas do bot com um caminho claro para o usuário concluir a tarefa.":::

* O bot instalado em um escopo de chat de canal ou grupo não deve enviar uma mensagem de boas-vindas proativa a todos os membros da equipe no chat 1:1. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-send-proactive-message-to-all-members.png" alt-text="O gráfico mostra um exemplo de bot enviando uma mensagem de boas-vindas proativa para todos os membros da equipe.":::

* Somente o bot de notificação poderá enviar uma mensagem de boas-vindas proativa em um canal somente se a mensagem contiver informações importantes para qualquer usuário concluir a configuração do bot ou esclarecer os cenários quando as notificações forem disparadas. [*Correção Obrigatória*]

* O bot instalado em um canal ou escopo de chat em grupo não deve enviar mensagens proativas (não apenas uma mensagem de boas-vindas) irrelevantes para todos os usuários no chat de canal ou grupo, em vez disso, deve enviar mensagens proativas ao usuário durante o chat 1:1. [*Correção Obrigatória*]

* O bot instalado em um escopo de chat de canal ou grupo não deve permitir que os usuários iniciem fluxos de trabalho individuais. Os bots devem concluir fluxos de trabalho individuais em chat 1:1 com o usuário. [*Correção Obrigatória*]

* A mensagem de boas-vindas do bot deve chamar claramente as limitações relacionadas ao uso do bot no escopo instalado. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-messahe-with-app-limitation.png" alt-text="O gráfico mostra um exemplo de limitação do aplicativo na mensagem de boas-vindas do bot.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-messahe-without-app-limitation.png" alt-text="O gráfico mostra um exemplo de um bot sem limitação de aplicativo em uma mensagem de boas-vindas.":::

* A mensagem de boas-vindas deve disparar automaticamente na instalação do aplicativo em um escopo pessoal. Se o bot não enviar uma mensagem de boas-vindas em um escopo pessoal, o usuário será levar a um dead-end. Se o aplicativo não incluir um fluxo de trabalho de configuração complexo, é opcional para o desenvolvedor disparar uma mensagem de boas-vindas no escopo do canal ou chat em grupo. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-no-welcome-message-in-personal-scope.png" alt-text="O gráfico mostra um exemplo de bot que não envia uma mensagem de boas-vindas automaticamente no escopo pessoal.":::

* As mensagens de boas-vindas devem ser disparadas apenas uma vez na instalação do bot. As mensagens de boas-vindas não devem ser disparadas sempre que o usuário invoca o comando de ajuda. A resposta do comando de ajuda deve estar focada para incluir uma maneira de o usuário acessar a ajuda relacionada ao bot. [*Correção Obrigatória*]

* As mensagens de boas-vindas não devem ser disparadas com todos os comandos do bot. Isso é considerado spam. [*Correção Obrigatória*]

  :::image type="content" source="../../../../assets/images/submission/validation-welcome-message-trigger-for-any-command.png" alt-text="O gráfico mostra um exemplo de bot disparando uma mensagem de boas-vindas para qualquer comando.":::

* O conteúdo da mensagem de boas-vindas deve estar relacionado ao fluxo de trabalho do bot mencionado na descrição longa do aplicativo e no escopo da instalação. A mensagem de boas-vindas deve incluir o valor oferecido pelo bot aos usuários que instalaram o bot no canal, como configurar o bot e descrever brevemente todos os comandos de bot com suporte. [*Correção Obrigatória*]

* O bot não deve enviar várias mensagens de boas-vindas quando disparado na instalação do aplicativo. [*Correção Obrigatória*]

  :::image type="content" source="../../../../assets/images/submission/validation-bot-multiple-message-trigger-install.png" alt-text="O gráfico mostra um exemplo de bot disparando várias mensagens de boas-vindas na instalação do aplicativo.":::

* O nome do aplicativo na mensagem de boas-vindas deve corresponder ao nome do aplicativo no manifesto. [*Correção Obrigatória*]

  :::image type="content" source="../../../../assets/images/submission/validation-app-name-mismatch-manifeast-and-welcome-message.png" alt-text="O gráfico mostra um exemplo de nome de aplicativo na mensagem de boas-vindas que não corresponde ao nome do aplicativo no manifesto do aplicativo.":::

* A mensagem de boas-vindas não deve exibir nomes de plataforma colaborativa baseadas em chat do concorrente, a menos que o aplicativo forneça interoperabilidade específica.

* A mensagem de boas-vindas não deve redirecionar o usuário para outro aplicativo do Teams, em vez disso, a mensagem de boas-vindas deve deslocar o usuário para concluir sua primeira tarefa e descrever brevemente todos os comandos de bot com suporte no aplicativo. [*Correção Obrigatória*]

* A mensagem de boas-vindas não deve conter links para nenhum marketplace de aplicativos, incluindo o AppSource. [*Correção Obrigatória*]

* Se seu aplicativo tiver um fluxo de trabalho de configuração complexo que exija a instalação do administrador, não tiver um fluxo de inscrição intuitivo e prontamente disponível ou exigir que os usuários concluam as etapas de configuração fora da experiência do Teams e retornem, o bot deverá enviar uma mensagem de boas-vindas proativa em um escopo de chat de equipe ou grupo após a instalação. [*Correção Obrigatória*]

* Se o bot enviar uma mensagem de boas-vindas no canal, ele não deverá enviá-la aos usuários individualmente (isso é considerado spam). A mensagem de boas-vindas também deve mencionar a pessoa que adicionou o bot. [*Correção Sugerida*]

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
  * Não envie várias mensagens em sucessão rápida.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-multiple-message-quick-succession.png" alt-text="O gráfico mostra um exemplo de um bot enviando várias mensagens em sucessão rápida.":::

  * Envie uma mensagem com informações completas.
  * Evite conversas de vários turnos para concluir um único fluxo de trabalho repetitivo.
  * Use um formulário (ou módulo de tarefa) para coletar todas as entradas de um usuário de uma só vez.
  * Chatbots conversacionais baseados em NLP podem usar conversas de vários turnos para tornar a discussão mais envolvente e concluir um fluxo de trabalho.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-using-task-module.png" alt-text="validation-bot-message-using-task-module":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-using-mutliple-conversation.png" alt-text="O gráfico mostra um bot de exemplo usando mensagens de vários turnos para concluir uma única conversa.":::

* **Mensagens de boas-vindas**: não repita a mesma mensagem de boas-vindas em intervalos regulares. Por exemplo, quando um novo membro é adicionado a uma equipe, não crie spam para outros membros com uma mensagem de boas-vindas. Envie uma mensagem ao novo membro pessoalmente.

   :::image type="icon" source="../../../../assets/images/submission/validation-bot-send-proactive-message-to-all-members.png" alt-text="O gráfico mostra um exemplo de spam de bot para usuários com a mesma mensagem de boas-vindas.":::

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

Aplicativos que fornecem apenas notificações com conteúdo, **como, Você** tem uma nova notificação **, clique** para exibir e exigir que o usuário navegue fora do Teams para que tudo o resto não forneça valor significativo no Teams.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-notification-only-inadequete-info.png" alt-text="A captura de tela mostra um exemplo de um bit de notificação apenas com informações inadequadas na visualização.":::

> [!TIP]
> Visualize as informações e forneça ações básicas do usuário embutido no cartão postado para que o usuário não seja necessário navegar para fora do Teams para todas as ações (independentemente da complexidade).

</details>
<br/>

<details><summary>Informações de metadados do bot</summary>

* As informações do bot no manifesto do aplicativo (nome do bot, logotipo, link de privacidade e link de termos de serviço) devem ser consistentes com os metadados do Bot Framework. [*Correção Obrigatória*]

* A ID do bot deve corresponder no manifesto do aplicativo e nos metadados do Bot Framework. [*Correção Obrigatória*]

* Verifique se a ID do bot no manifesto do aplicativo corresponde à ID do bot na última versão publicada da loja do seu aplicativo. A alteração de IDs de bot em uma atualização de aplicativo leva à perda permanente de todo o histórico de interação do usuário com o bot para usuários existentes do seu aplicativo e inicia uma nova cadeia de conversa com a nova ID do Bot. [*Correção Obrigatória*]

* Qualquer alteração no nome do aplicativo, metadados, mensagem de boas-vindas do bot ou respostas de bot deve ser atualizada com o novo nome. [*Correção Obrigatória*]

* O nome do aplicativo na mensagem de boas-vindas do bot ou as respostas do bot devem corresponder ao nome do aplicativo no manifesto. [*Correção Obrigatória*]

</details>
<br/>

<details><summary>Bot no escopo colaborativo</summary>

* A instalação do bot em um escopo de chat de canal ou grupo para obter a lista de participantes da equipe para enviar notificações proativas para os usuários como chats 1:1 para gatilhos específicos da equipe não é permitida. Por exemplo, aplicativo que emparelha pessoas para um encontro. [*Correção Obrigatória*]

* O bot no chat em grupo ou canal usado apenas para obter as mensagens ou postagens no chat de canal ou grupo para enviar notificações proativas para os usuários, pois chats 1:1 não são permitidos. [*Correção Obrigatória*]

* Os bots instalados no escopo colaborativo devem fornecer um valor de usuário no escopo colaborativo. [*Correção Obrigatória*]

</details>

## <a name="message-extensions"></a>Extensões de mensagens

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.4](/legal/marketplace/certification-policies#114044-messaging-extensions).

Se o aplicativo incluir uma extensão de mensagem, verifique se ele segue essas diretrizes.

> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, consulte as [diretrizes de design de extensão de mensagens do Teams](~/messaging-extensions/design/messaging-extension-design.md).

<br/>

<details><summary>Diretrizes de design das extensões de mensagens</summary>

* Se o aplicativo Teams usar a funcionalidade de extensão de mensagens, seu aplicativo deverá seguir as [diretrizes de design](../../../../messaging-extensions/design/messaging-extension-design.md) da extensão mensagens.

   :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-design-guidelines-fail.png" alt-text="O gráfico mostra um exemplo de um aplicativo que não está a atender às diretrizes de extensão.":::

* Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa. Mantenha sua extensão de mensagens simples e exiba apenas os componentes necessários para concluir efetivamente a ação. O site completo não deve ser enquadrado na extensão de mensagens [*Correção obrigatória*]

* As imagens de visualização em Cartões Adaptáveis em extensões de mensagens devem ser carregadas corretamente. [*Correção Obrigatória*]

  :::image type="content" source="../../../../assets/images/submission/validation-preview-image-adaptive-card-loading.png" alt-text="O gráfico mostra um exemplo de carregamento de imagem de visualização no cartão adaptável.":::

  :::image type="content" source="../../../../assets/images/submission/validation-preview-image-adaptive-card-not-loading.png" alt-text="O gráfico mostra um exemplo de imagem de visualização não carregando no cartão adaptável.":::

* O cartão de resposta da extensão de mensagens deve incluir o ícone do aplicativo para evitar confusão do usuário final. [*Correção Obrigatória*]

* Seu aplicativo não deve ter nenhuma funcionalidade quebrada. O aplicativo não deve encerrar ou impedir que o usuário conclua um fluxo de trabalho em uma extensão de mensagens. [*Correção Obrigatória*]

* As extensões de mensagens devem responder ou funcionar conforme o esperado nos escopos de chat e canal do grupo. [*Correção Obrigatória*]

* Você deve incluir uma maneira de o usuário entrar ou sair da extensão de mensagens. [*Correção Obrigatória*]

</details>
</br>

<details><summary>Comandos de ação para extensões de mensagem baseadas em ação</summary>

As extensões de mensagens baseadas em ação devem fazer o seguinte:

* Permitir que os usuários disparem ações em uma mensagem sem concluir etapas intermediárias, como entrar.

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-no-intermediate-step.png" alt-text="validation-messaging-extension-no-intermediate-steps":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-intermediate-step-available.png" alt-text="validation-messaging-extension-intermediate-steps-available":::

* Transferir o contexto da mensagem ao próximo estado de trabalho. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-app-passes-message.png" alt-text="validation-messaging-extension-app-passes-messages":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-app-doesnot-pass-message.png" alt-text="validation-messaging-extension-app-doesnot-pass-messages":::

* Incorpore o nome do aplicativo host em vez de um verbo genérico para comandos de ação disparados de uma mensagem de chat, postagem de canal ou chamada para ação em aplicativos. Por exemplo, use **Iniciar um Reunião do Skype** **para Iniciar** Reunião, **Carregar arquivo no DocuSign** para **Carregar arquivo**. [*Correção Sugerida*]

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-action-command-host-name.png" alt-text="O gráfico mostra um exemplo de nome do aplicativo host para um comando de ação.":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-action-command-verb.png" alt-text="O gráfico mostra um exemplo de verbo genérico para um comando de ação.":::

* Invocar uma ação de mensagem deve permitir que o usuário conclua o fluxo de trabalho. Erros, respostas em branco ou indicadores de carregamento contínuo para tornar a ação da mensagem funcional conforme o esperado não devem estar presentes. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-continous-loading-indicator-action-command.png" alt-text="O gráfico mostra um exemplo de indicador de carregamento contínuo quando um bot invoca um comando de ação.":::

* Os comandos de ação duplicados não devem estar presentes. [*Correção Obrigatória*]

* As ações de mensagem devem permitir que o usuário conclua o fluxo de trabalho conforme o esperado sem uma resposta inválida. [*Correção Obrigatória*]

* Os aplicativos com apenas a extensão de mensagens baseada em ação devem ter o seguinte estado final:

  * Poste uma ação relevante como uma notificação no contexto em que a extensão de mensagem é invocada ou no chat de bot 1:1 com base no cenário do usuário. [*Correção Obrigatória*]

  * Permitir que os usuários compartilhem cartões com outros usuários com base na ação executada. Isso é para garantir que os aplicativos não executem ações silenciosas. Por exemplo, um tíquete é criado com base em uma mensagem em um canal, mas o aplicativo não envia uma notificação ou não fornece uma maneira de solicitar que o usuário compartilhe detalhes do tíquete após a criação do tíquete. [*Correção Obrigatória*]

</details>
</br>

<details><summary>Links de visualização (desenrolar do link)</summary>

[*Correção Obrigatória*]

As extensões de mensagens devem visualizar links reconhecidos na caixa de redação do Teams. Não adicione domínios que estão fora do seu controle (URLs absolutas ou curingas). Por exemplo, `yourapp.onmicrosoft.com` é válido, `*.onmicrosoft.com` não é válido. Domínios de nível superior também são proibidos. Por exemplo: `*.com` ou `*.org`. [*Correção Obrigatória*]

</details>
</br>

<details><summary>Comandos de pesquisa</summary>

* Extensões de mensagens baseadas em pesquisa devem fornecer texto que ajude os usuários a pesquisar com eficiência. [*Correção Obrigatória*]

    :::image type="content" source="../../../../assets/images/submission/validation-search-commands-text-available.png" alt-text="O gráfico mostra um exemplo de uma extensão de mensagem com texto de ajuda para que os usuários pesquisem com eficiência.":::

    :::image type="content" source="../../../../assets/images/submission/validation-search-commands-text-not-available.png" alt-text="O gráfico mostra um exemplo de uma extensão de mensagem sem texto de ajuda para que os usuários pesquisem com eficiência.":::

* @menções executáveis devem ser claras, fáceis de entender, e acessíveis.

    :::image type="content" source="../../../../assets/images/submission/validation-search-command-unclear-executable.png" alt-text="validation-search-commands-unclear-executable":::

</details>
</br>

<details><summary>Comandos de ação para extensão de mensagem baseada em pesquisa</summary>

[*Correção Obrigatória*]

Os aplicativos que consistem na extensão de mensagens baseada em pesquisa fornecem valor ao usuário compartilhando cartões que permitem conversas contextuais sem alternância de contexto.

Para passar a validação para um aplicativo somente de extensão de mensagem baseado em pesquisa, os itens a seguir são necessários como linha de base para garantir que a experiência do usuário não seja interrompida. Um cartão compartilhado por meio de uma extensão de mensagens fornecerá valor no Teams se:

1. O cartão postado fornece detalhes adequados que não exigem mais nenhuma ação do usuário.
1. O cartão postado fornece informações de visualização adequadas para um usuário executar uma ação ou decidir exibir mais detalhes em um link que abre fora do Teams.

    :::image type="content" source="../../../../assets/images/submission/validation-search-based-messaging-ext-adequete-info.png" alt-text="validation-search-base-messaging-ext-adequete-info":::

    :::image type="content" source="../../../../assets/images/submission/validation-search-based-messaging-ext-inadequete-info.png" alt-text="validation-search-base-messaging-ext-inadequete-info":::

Os aplicativos de desbloqueio de links não fornecem um valor significativo para as equipes. Considere a criação de fluxos de trabalho adicionais em seu aplicativo, se seu aplicativo só oferece suporte para o desenrolamento de link e não tem nenhuma outra funcionalidade.

</details>

## <a name="task-modules"></a>Módulos de tarefas

[*Correção Obrigatória*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.5](/legal/marketplace/certification-policies#114045-task-modules).
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

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.6](/legal/marketplace/certification-policies#114046-meeting-extensions).
> [!TIP]
> Para obter mais informações sobre como criar uma experiência de aplicativo de alta qualidade, confira as [diretrizes de design de extensão de reunião do Teams](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

</br>
<details><summary>Diretrizes de design de extensão de reunião</summary>

* Seus aplicativos do Teams devem seguir [as diretrizes de design da extensão de reunião](../../../../apps-in-teams-meetings/design/designing-apps-in-meetings.md).

* Com a experiência do aplicativo na reunião, você pode envolver os participantes durante a reunião usando guias na reunião, caixa de diálogo e o compartilhamento na reunião para preparar o recurso. Se seu aplicativo der suporte à extensão de reunião do Teams, você deverá fornecer uma experiência de reunião responsiva alinhada com a experiência de reunião do Teams. [*Correção Obrigatória*]

* Com a experiência de aplicativo de pré-reunião, os usuários podem encontrar e adicionar aplicativos de reunião. Os usuários também podem realizar tarefas de pré-reunião, como desenvolver uma votação para pesquisar os participantes da reunião. Um aplicativo que fornece uma experiência de pré-reunião deve ser relevante para o fluxo de trabalho de reunião e oferecer valor ao usuário. [*Correção Obrigatória*]

* Com a experiência do aplicativo pós-reunião, os usuários podem exibir os resultados da reunião, como resultados da pesquisa ou comentários e outros conteúdos do aplicativo. Um aplicativo que fornece uma experiência pós-reunião deve ser relevante para o fluxo de trabalho da reunião e oferecer valor ao usuário. [*Correção Obrigatória*]

* Com a experiência do aplicativo na reunião, você pode envolver os participantes da reunião durante a reunião e aprimorar a experiência de reunião para todos os participantes. Os participantes não devem ser levados para fora da reunião do Teams para concluir os fluxos de trabalho principais do usuário do aplicativo. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-outside-teams-core-workflows.png" alt-text="O gráfico mostra um exemplo de uma experiência na reunião redirecionando o usuário para fora do Teams para concluir a funcionalidade principal do aplicativo.":::

* Seu aplicativo deve oferecer valor além de fornecer apenas cenas personalizadas do Modo Juntos no Teams. [*Correção Obrigatória*]

* Você deve declarar `groupChat` como um escopo em `configurableTabs` e `meetingDetailsTab`, e `meetingChatTab``meetingSidePanel` como uma propriedade de contexto no manifesto para habilitar seu aplicativo para reuniões no teams mobile. [*Correção Obrigatória*]

* As telas de reunião não devem encerrar um participante da reunião. As telas de reunião devem mostrar uma mensagem de falha normal para limitações do aplicativo, como dependência específica da região. [*Correção Obrigatória*]

* O cabeçalho da tela da reunião deve exibir o nome do aplicativo correto para evitar confundir o participante da reunião. [*Correção Obrigatória*]

* Você deve incluir uma opção para o usuário sair ou sair da extensão da reunião. [*Correção Obrigatória*]

* As guias de reunião em plataformas móveis devem incluir fluxos de trabalho relevantes. Páginas em branco não devem estar presentes em uma guia de reunião. [*Correção obrigatória*]

* O estágio de reunião é uma tela de participação focada, intuitiva e colaborativa. O estágio da reunião não deve inserir a experiência completa do site. [*Correção Obrigatória*]

* O aplicativo não deve mostrar a tela de carregamento contínuo, o erro ou a funcionalidade interrompida que encerra o usuário ou bloqueia a conclusão de um fluxo de trabalho em um cenário de reunião. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-app-shows-continous-loading-screen.png" alt-text="O gráfico mostra um exemplo de tela de carregamento contínuo em um aplicativo.":::

* O aplicativo não deve abrir uma nova instância do Teams ao iniciar uma reunião. As telas de reunião são uma extensão dos recursos do Teams que promovem a colaboração em tempo real e novas reuniões sempre devem ser abertas na instância ativa do Teams no momento. [*Correção Obrigatória*]

* Os aplicativos de reunião devem concluir fluxos de trabalho na plataforma do Microsoft Teams sem redirecionar para plataformas de chat concorrentes. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-apps-redirecting-competitor-chat-platform.png" alt-text="O gráfico mostra um exemplo de um aplicativo redirecionando para a plataforma baseada em chat concorrente.":::

* Se seu aplicativo der suporte a exibições baseadas em função e determinados fluxos de trabalho estiverem indisponíveis para todos os participantes, recomendamos que você implemente o sistema de mensagens adequado para os participantes na guia e no painel lateral informando que o aplicativo está atualmente para exibição do organizador e fornece detalhes sobre como os participantes receberão as anotações da reunião, os itens de ação e as agendas de atualização. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-way-forward-not-available-for-role-based-views.png" alt-text="O gráfico mostra um exemplo de um aplicativo sem uma maneira de avançar para os participantes em uma exibição baseada em função.":::

</details>
<br/>

<details><summary>Geral</summary>

Use as seguintes diretrizes para extensões de reunião:

* Os aplicativos de extensibilidade de reunião devem oferecer uma experiência responsiva na reunião alinhada à experiência de reunião do Teams. A experiência na reunião é obrigatória para um aplicativo do Teams que dá suporte à extensibilidade de reuniões, mas as experiências pré e pós-reunião não são obrigatórias.

  * Com a experiência de aplicativo de pré-reunião, os usuários podem encontrar e adicionar aplicativos de reunião. Os usuários também podem executar tarefas de pré-reunião, como desenvolver uma votação para pesquisar os participantes da reunião. Se seu aplicativo fornecer uma experiência de pré-reunião, ele deverá ser relevante para o fluxo de trabalho da reunião.

  * Com a experiência do aplicativo pós-reunião, os usuários podem exibir os resultados da reunião, como resultados da pesquisa ou comentários e outros conteúdos do aplicativo. Se seu aplicativo fornecer uma experiência pós-reunião, ele deverá ser relevante para o fluxo de trabalho da reunião.

  * Com a experiência do aplicativo na reunião, você pode envolver os participantes da reunião durante a reunião e aprimorar a experiência de reunião para todos os participantes. Os participantes não devem ser retirados da reunião do Teams para concluir os fluxos de trabalho principais do usuário do seu aplicativo.

* Seu aplicativo deve oferecer valor além de fornecer cenas personalizadas do Modo Conferência no Teams.

* O recurso de estágio de reunião compartilhada só pode ser iniciado por meio do aplicativo da área de trabalho do Teams. No entanto, a experiência de consumo do estágio de reunião compartilhada deve ser utilizável e não interrompida quando exibida em dispositivos móveis.

> [!TIP]
> Você deve declarar `groupChat` como um escopo em `configurableTabs` e `meetingDetailsTab`, e `meetingChatTab``meetingSidePanel` como uma propriedade de contexto no manifesto para habilitar seu aplicativo para reuniões no teams mobile.

</details>
</br>

<details><summary>Experiência de pré e pós-reunião</summary>

* As telas de pré e pós-reunião devem seguir as diretrizes gerais de design de guia. Para obter mais informações, confira [diretrizes de design do Teams](~/tabs/design/tabs.md).
* As guias devem ter um layout organizado ao exibir vários itens. Por exemplo, mais de 10 enquetes ou pesquisas, veja o [layout de exemplo](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Seu aplicativo deve notificar os usuários quando os resultados de uma pesquisa ou votação são exportados, declarando **Resultados baixados com êxito**.

   :::image type="content" source="../../../../assets/images/submission/validation-meeting-experience-tab-design-guidelines-fail.png" alt-text="O gráfico mostra um exemplo de guia que não está seguindo as diretrizes de design da guia.":::

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

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-back-button.png" alt-text="O gráfico mostra um exemplo do botão Voltar presente.":::

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-back-button-absent.png" alt-text="O gráfico mostra um exemplo de botão Voltar não presente.":::

* Não deve incluir mais de um botão fechar. Isso pode confundir os usuários, pois já existe um botão de cabeçalho interno para ignorar a guia.
* Não deve ter rolagem horizontal.

  :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-tab-vertical-scroll.png" alt-text="O gráfico mostra um exemplo de guia na reunião com rolagem vertical.":::

  :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-tab-horizontal-scroll.png" alt-text="O gráfico mostra um exemplo de guia na reunião com rolagem horizontal.":::

</details>

</br>
<details><summary>Caixas de diálogo na reunião</summary>

* Deve ser usado com moderação e para cenários que são leves e orientados a tarefas.
* Deve exibir o conteúdo em uma única coluna e não possuir vários níveis de navegação.

  :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-single-column-layout.png" alt-text="O gráfico mostra um exemplo de layout de coluna única para a caixa de diálogo na reunião.":::

  :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-multiple-column-layout.png" alt-text="O gráfico mostra um exemplo de vários layouts de coluna para a caixa de diálogo na reunião.":::

* Não deve usar módulos de tarefa.
* Deve alinhar-se ao centro do estágio da reunião.

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-dialog-not-aligned.png" alt-text="O gráfico mostra um exemplo de caixa de diálogo na reunião que não está alinhada com o centro do estágio de reunião.":::

* Deve ser ignorado depois que um usuário seleciona um botão ou executa uma ação.

* **Modo Conferência**: considere as seguintes práticas recomendadas para uma experiência de criação de cena:
  * Todas as imagens estão no formato .png.
  * O pacote final com todas as imagens juntas não deve exceder a resolução 1920x1080. A resolução é um número par. Essa resolução é um requisito para que as cenas sejam mostradas com êxito.
  * O tamanho máximo da cena é de 10 MB.
  * O tamanho máximo de cada imagem é de 5 MB. Uma cena é uma coleção de várias imagens. O limite é para cada imagem individual.
  * Selecione **Transparente** conforme necessário. Essa caixa de seleção está disponível no painel direito quando uma imagem é selecionada. As imagens sobrepostas devem ser marcadas como Transparentes para indicar que estão sobrepondo imagens na cena.

</details>

## <a name="notifications"></a>Notificações

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.4.7](/legal/marketplace/certification-policies#114047-notification-apis).

Se seu aplicativo usar as [APIs de feed](/graph/teams-send-activityfeednotifications) de atividades fornecidas pelo Microsoft Graph, verifique se ele segue as diretrizes a seguir.

> [!TIP]
> Se seus aplicativos dão suporte a cenários de notificação em que as notificações são disparadas após intervalos longos, por exemplo, após um dia ou um mês. Antes de enviar para revisão, certifique-se de disparar essas notificações em segundo plano para que testemos as notificações.

<br></br>

<details><summary>Diretrizes de design de notificação</summary>

* Seus aplicativos do Teams devem seguir [as diretrizes de design de notificações do feed de atividades](/graph/teams-send-activityfeednotifications).

* O fluxo de trabalho irrelevante, inadequado, sem resposta ou interrompido não deve estar presente depois que o usuário seleciona uma notificação no feed de atividades do Teams. Os usuários não devem ser impedidos de concluir um fluxo de trabalho depois de selecionarem uma notificação do feed de atividades. [*Correção Obrigatória*]

* Inclua o nome do aplicativo na notificação do feed de atividades para que os usuários finais entendam a origem ou o gatilho da notificação sem confusão. [*Correção Obrigatória*]

* O aplicativo deve disparar notificações para todos os cenários de notificação mencionados na descrição longa do aplicativo, experiência de primeira execução do aplicativo e em cenários declarados `activityTypes` no manifesto. [*Correção Obrigatória*]

* As notificações devem ser exibidas em cinco segundos a partir da ação do usuário. [*Correção Obrigatória*]

* Você deve chamar as limitações de notificação (se houver) na descrição longa do aplicativo ou na primeira experiência de execução do aplicativo. [*Correção Obrigatória*]

</details>
<br/>

<details><summary>Geral</summary>

* Todos os gatilhos de notificação especificados na configuração do aplicativo devem funcionar.
* As notificações devem ser localizadas de acordo com os idiomas suportados configurados no seu aplicativo.
* As notificações devem ser exibidas em cinco segundos a partir da ação do usuário.
* As notificações devem ser localizadas de acordo com os idiomas com suporte para todas as plataformas em que seu aplicativo é compatível. [*Correção Obrigatória*]

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

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.6](/legal/marketplace/certification-policies#11406-publisher-attestation).
<br></br>
<details><summary>Expanda para saber mais</summary>

O Programa de Conformidade dos Aplicativos do Microsoft 365 tem como objetivo ajudar as organizações a avaliarem e gerenciarem riscos através da avaliação de informações de segurança e conformidade do seu aplicativo. Se você publicar um aplicativo na loja do Teams, precisará concluir os seguintes níveis do programa:

* **Verificação do Editor**: ajuda os administradores e usuários finais a entenderem a autenticidade dos desenvolvedores de aplicativos que se integram à plataforma de identidade da Microsoft. Quando concluído, um selo azul **verificado** é exibido na caixa de diálogo de consentimento Azure Active Directory e em outras telas. Para obter mais informações, consulte [Marcar seu aplicativo como verificado pelo editor](/azure/active-directory/develop/mark-app-as-publisher-verified).

    :::image type="content" source="../../../../assets/images/submission/validation-365-compliance-publisher-verification.png" alt-text="O gráfico mostra um exemplo de uma notificação azul verificada na caixa de diálogo de consentimento do Azure Active Directory.":::

* **Atestado do Editor**: um processo no qual você compartilha informações gerais, de tratamento de dados, e de segurança e conformidade para ajudar os clientes em potencial a tomarem decisões informadas sobre como usar seu aplicativo.

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png"::: Se você estiver enviando um aplicativo que não foi listado anteriormente, não poderá concluir oficialmente o Atestado de Editor até que seu aplicativo esteja na loja do Teams. Se você atualizar um aplicativo listado, conclua o Atestado do Editor antes de enviar a versão mais recente do aplicativo.

</details>

## <a name="advertising"></a>Publicidade

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Esta seção está alinhada com a [política do marketplace comercial da Microsoft número 1140.7](/legal/marketplace/certification-policies#11407-advertising).

Os aplicativos não devem exibir anúncios, incluindo anúncios dinâmicos, anúncios em faixa e anúncios na mensagem.

:::image type="content" source="../../../../assets/images/submission/validation-advertising-banners.png" alt-text="O gráfico mostra um exemplo de um cenário com falha de publicidade no Teams.":::

## <a name="cryptocurrency-based-apps"></a>Aplicativos baseados em criptografia

Você deve demonstrar a conformidade com todas as leis em que seu aplicativo é distribuído, se seu aplicativo:

* Facilita transações ou transmissões de criptografia dentro do aplicativo.

* Promove o conteúdo relacionado à criptografia.

* Permite que os usuários armazenem ou acessem suas criptografias armazenadas.

* Incentiva ou permite que os usuários concluam uma transação ou transmissão baseada em criptografia fora da plataforma teams.

* Incentiva ou facilita a mineração de tokens de criptografia.

* Facilita a participação do usuário em ofertas iniciais de moedas.

* Recompensa ou incentiva os usuários com tokens de criptografia para concluir uma tarefa.

Após uma revisão interna da Microsoft, se a demonstração de conformidade for satisfatória, a Microsoft poderá prosseguir com a certificação adicional do seu aplicativo. Se a demonstração de conformidade for insatisfatória, a Microsoft manterá você informado sobre a decisão de não prosseguir com a certificação do seu aplicativo.

## <a name="app-functionality"></a>Funcionalidade do aplicativo

* Fluxos de trabalho ou conteúdo no aplicativo devem estar relacionados ao escopo. [*Correção Obrigatória*]
* Todas as funcionalidades do aplicativo devem ser funcionais e devem funcionar corretamente, conforme descrito na descrição longa do appSource ou do manifesto. [*Correção Obrigatória*]
* Os aplicativos sempre devem intimar o usuário antes de baixar qualquer arquivo ou executável no ambiente do usuário. Qualquer CTA (chamada para ação), baseada em texto ou não, que deixa claro para o usuário que um arquivo ou executável é baixado na ação do usuário é permitido no aplicativo. [*Correção Obrigatória*]

## <a name="mobile-experience"></a>Experiência móvel

* Os suplementos móveis devem ser gratuitos. Não deve haver nenhum conteúdo no aplicativo ou links que promovam venda adicional, lojas online ou outras solicitações de pagamento. Todas as contas necessárias para aplicativos não devem ter nenhum custo para uso e, se o tempo for limitado, não devem incluir nenhum conteúdo que indique a necessidade de pagamento.

   :::image type="content" source="../../../../assets/images/submission/validation-mobile-add-in-charges.png" alt-text="O gráfico mostra um exemplo de um suplemento móvel solicitando pagamento.":::

* O uso da palavra **FREE**, **FREE TRIAL** ou **TRY FREE** é permitido na experiência de aplicativo Web ou desktop sem nenhuma limitação ou consideração.

* O uso da palavra **FREE** como texto sem formatação no contexto de uma avaliação ou atualização de aplicativo é permitido em dispositivos móveis.

* O uso da palavra **GRATUITA** no contexto de uma avaliação ou atualização de aplicativo com um link que leva a uma página de aterrissagem sem informações de pagamento ou preços é permitido no celular. Texto sem formatação para sinalizar que **o aplicativo é PAGO** é permitido no celular.

* O uso da palavra **FREE** como texto sem formatação no contexto de uma atualização de aplicativo ou avaliação e associado a detalhes de preços não é permitido no celular.

* Não é permitido o uso da palavra **FREE** no contexto de uma avaliação ou atualização de aplicativo e associado a um link que leva a uma página de aterrissagem com informações de preços ou detalhes de pagamento no celular.

* Detalhes de preços em dispositivos móveis em qualquer formato, por exemplo, imagem, texto ou link não são permitidos. CTA, como **planos de exibição** em dispositivos móveis, não é permitido. Informações sobre planos sem detalhes de preços, mas com um link de contato ou email no celular não são permitidas. Qualquer texto com detalhes de contato vinculando ou aludindo a uma atualização paga não é permitido em dispositivos móveis. Pagamentos para bens físicos são permitidos em dispositivos móveis. Por exemplo, seu aplicativo pode permitir o pagamento para reservar um táxi.

   :::image type="content" source="../../../../assets/images/submission/validation-mobile-exp-pricing-details-on-mobile-fail.png" alt-text="O gráfico mostra um exemplo de detalhes de preços em dispositivos móveis.":::

* Pagamentos para bens digitais no aplicativo não são permitidos no celular. [*Correção Obrigatória*]

   :::image type="content" source="../../../../assets/images/submission/validation-mobile-exp-payments-digital-goods.png" alt-text="O gráfico mostra um exemplo de pagamentos de bens digitais em dispositivos móveis.":::

* Os aplicativos do Teams devem oferecer uma experiência móvel apropriada entre dispositivos. [*Correção Obrigatória*]

* Os recursos que não têm suporte em dispositivos móveis não devem encerrar um usuário e devem fornecer uma mensagem de falha normal quando aplicável. [*Correção Obrigatória*]

## <a name="next-step"></a>Próxima etapa

> [!div class=*nextstepaction*]
> [Criar uma conta do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)

## <a name="see-also"></a>Confira também

* [Distribuir seu aplicativo](~/concepts/deploy-and-publish/apps-publish-overview.md)
* [Preparar o envio para a Microsoft Store](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [Testar e depurar seu aplicativo](~/concepts/build-and-test/debug.md)
* [Criar uma conta de desenvolvedor do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
