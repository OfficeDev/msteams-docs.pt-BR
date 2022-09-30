---
title: Incluir uma oferta SaaS com seu aplicativo
description: Saiba como monetizar seu aplicativo Microsoft Teams vendendo planos de assinatura diretamente da listagem da loja do Teams. Entenda como publicar aplicativo, usuário final, experiência de compra de administrador.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: 23327ea2765eb5496f8cfb157cdd194fcc13aaf7
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243252"
---
# <a name="include-a-saas-offer-with-your-teams-app"></a>Incluir uma oferta de SaaS com seu aplicativo Teams

:::row:::
   :::column span="3":::

Com uma oferta de Software como serviço (SaaS) transacionável, você pode monetizar seu aplicativo do Teams por meio da venda de planos de assinatura diretamente da listagem da loja do Teams. Por exemplo, digamos que você tenha um aplicativo gratuito que qualquer pessoa pode obter na loja. Agora você pode oferecer planos premium e empresariais para usuários que querem mais recursos.

Aqui está uma ideia geral de como monetizar seu aplicativo:

1. [Planeje sua oferta de SaaS](#plan-your-saas-offer).

1. [Integre às APIs de atendimento SaaS](#integrate-with-the-saas-fulfillment-apis).

1. [Crie uma página inicial para gerenciamento de assinatura](#build-a-landing-page-for-subscription-management).

1. [Crie sua oferta de SaaS](#create-your-saas-offer).

1. [Configure seu aplicativo para a oferta de SaaS](#configure-your-app-for-the-saas-offer).

1. [Publique seu aplicativo na loja do Teams](#publish-your-app).

   :::column-end:::
   :::column span="1":::

:::image type="content" source="~/assets/images/saas-offer/saas-offer-diagram.png" alt-text="Diagrama mostrando o processo de como incluir uma oferta de SaaS com seu aplicativo do Teams.":::

   :::column-end:::
:::row-end:::

## <a name="plan-your-saas-offer"></a>Planejar a oferta de SaaS

Para obter diretrizes abrangentes, [consulte como planejar uma oferta de SaaS para o marketplace comercial da Microsoft](/azure/marketplace/plan-saas-offer).

Ao planejar como monetizar seu aplicativo do Teams, aqui estão algumas coisas a considerar:

* Decida o modelo de assinatura. Uma oferta SsaaS transacional pode incluir vários planos de assinatura. Os planos de assinatura pública disponíveis para qualquer pessoa são mais comuns, mas você também pode querer direcionar clientes específicos com ofertas apenas para eles. Para obter mais informações, consulte [planos privados no marketplace comercial da Microsoft](/azure/marketplace/private-plans).
* Leia sobre a opção [*Vender por meio da Microsoft*](/azure/marketplace/plan-saas-offer#listing-options) para sua oferta do SaaS, que é necessária se você quiser que os usuários comprem planos de assinatura para seu aplicativo diretamente por meio da loja do Teams.
* Saiba como o [Azure Active Directory SSO (login único)](/azure/marketplace/azure-ad-saas) ajuda seus clientes a comprar e gerenciar assinaturas. (Microsoft Azure Active Directory (Azure AD) SSO é necessário para aplicativos do Teams com ofertas SaaS.)
* Entenda que você é responsável pelo gerenciamento e pagamento da infraestrutura necessária para dar suporte ao uso da oferta de SaaS dos seus clientes.
* Planeje para dispositivos móveis. Para evitar violar políticas de armazenamento de aplicativos de terceiros, seu aplicativo não pode incluir links que permitem que os usuários comprem planos de assinatura em dispositivos móveis. No entanto, você ainda pode indicar se seu aplicativo tem recursos que exigem um plano de assinatura. Para obter mais informações, consulte as [políticas de certificação do mercado comercial](/legal/marketplace/certification-policies#114048-mobile-experience) relacionadas.

## <a name="integrate-with-the-saas-fulfillment-apis"></a>Integrar-se às APIs de atendimento de Saas

A integração com as APIs de atendimento de SaaS é necessária para monetizar seu aplicativo do Teams. Essas APIs ajudam você a gerenciar o ciclo de vida de um plano de assinatura após ele ser comprado por um usuário.

Para obter instruções completas e referência à API, consulte a documentação das [APIs de atendimento de SaaS](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-apis). Em geral, você implementará as etapas a seguir usando as APIs após uma assinatura for comprada:

1. Receba um [*token de identificação de compra*](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-life-cycle#purchased-but-not-yet-activated-pendingfulfillmentstart) por meio da URL para sua página inicial.

1. Use o token para recuperar detalhes da assinatura.

1. Notifique o marketplace comercial de que a assinatura está ativada.

### <a name="best-practices-for-implementing-subscription-management"></a>Práticas recomendadas para implementar o gerenciamento de assinaturas

* Com as ofertas de SaaS transacionáveis para aplicativos do Teams, os planos de assinatura (licenças) devem ser atribuídos a usuários individuais, em vez de grupos ou a uma organização inteira.
* Quando os usuários receberem um plano de assinatura, notifique-os por meio de um bot Teams ou email. Na mensagem, inclua informações sobre como adicionar o aplicativo ao Teams e começar.
* Suporte a ideia de vários administradores. Em outras palavras, vários usuários na mesma organização podem comprar e gerenciar suas próprias assinaturas.

## <a name="manage-license-for-third-party-apps-in-teams"></a>Gerenciar licença para aplicativos de terceiros no Teams

O Teams permite que administradores ou usuários independentes de ISVs (fornecedores de software) gerenciem licenças SaaS para aplicativos de terceiros adquiridos na vitrine do Teams. Os administradores ou usuários do ISV podem facilmente atribuir, cancelar a atribuição, usar e acompanhar licenças SaaS.

Para habilitar o gerenciamento de licenças para um aplicativo no Teams, siga as etapas:

1. [Criar uma oferta no Partner Center](#create-an-offer-in-partner-center)
1. [Atualizar seu aplicativo Teams](#update-your-teams-app)
1. [Pós-compra](#post-purchase)
1. [Integrar com a API de Uso correto do Graph](#integrate-with-graph-usage-right-api)

### <a name="create-an-offer-in-partner-center"></a>Criar uma oferta no Partner Center

1. Entre no [Partner Center e](https://partner.microsoft.com/) selecione **Partner Center**.

   :::image type="content" source="~/assets/images/first-party-license-mgt/partner-center-home-page.png" alt-text="As capturas de tela mostram como fazer logon na conta do Partner Center.":::

1. Na **home page** , selecione a guia **ofertas do Marketplace** para definir ofertas do marketplace comercial.

   :::image type="content" source="~/assets/images/first-party-license-mgt/home-page.png" alt-text="As capturas de tela mostram a home page e a guia oferta do Marketplace no Partner Center.":::

1. Selecione **Visão** geral no painel esquerdo.

1. Selecione **Novo** > **Software como Serviço de Oferta**.

   :::image type="content" source="~/assets/images/first-party-license-mgt/commercial-marketplace.png" alt-text="As capturas de tela mostram a página de oferta do marketplace em que você pode selecionar a nova oferta.":::

1. Insira **a ID da oferta** **e o alias da** oferta e selecione **Criar**.

   > [!NOTE]
   > Se você estiver criando uma oferta para fins de teste, adicione o texto **-ISVPILOT** ao final do alias da oferta. Isso indica à equipe de certificação que a oferta é para fins de teste. A Microsoft exclui ofertas **com -ISVPILOT** periodicamente. Portanto, não use essa marca por motivos diferentes de testar a funcionalidade de gerenciamento de licenças.

   :::image type="content" source="~/assets/images/first-party-license-mgt/saas.png" alt-text="As capturas de tela mostram como inserir a ID da oferta e o alias da oferta no Partner Center.":::

1. Na página Configuração da oferta, em detalhes de configuração, marque a caixa de seleção Sim, gostaria que a Microsoft gerenciando **licenças de cliente em meu nome**.

   :::image type="content" source="~/assets/images/first-party-license-mgt/saas-isvpilot.png" alt-text="As capturas de tela mostram a página de configuração da oferta para configurar a licença a ser gerenciada para seu aplicativo no Teams.":::

   > [!NOTE]
   >
   > * Essa é uma configuração única e você não poderá alterá-la depois que sua oferta for publicada. Isso permite que o cliente gerencie licenças para seu aplicativo no Teams.
   > * O manifesto do aplicativo dá suporte a apenas uma oferta para um aplicativo. Escolha uma solução de gerenciamento de licença apropriada para todos os planos disponíveis em sua oferta e você não poderá alterar essa opção depois que a oferta for enviada por push.

1. Selecione **Salvar rascunho**.

1. Selecione **Visão geral do** plano no painel esquerdo e, em seguida, **selecione Criar novo plano**.

   > [!NOTE]
   > Você precisa adicionar pelo menos um plano.

   :::image type="content" source="~/assets/images/first-party-license-mgt/plan-overview.png" alt-text="As capturas de tela mostram a visão geral do plano para criar um novo plano para seus aplicativos no Partner Center.":::

1. Insira a ID do Plano e o nome do plano e selecione **Criar**.

1. Insira o **nome do plano e** a **descrição do plano**.

   > [!NOTE]
   > As informações do plano são exibidas no marketplace do Teams e [no Appsource](https://appsource.microsoft.com/) na listagem de ofertas (seção planos).

   :::image type="content" source="~/assets/images/first-party-license-mgt/plan-listing.png" alt-text="As capturas de tela mostram a página de plano para adicionar o nome do plano e a descrição do plano para seu aplicativo.":::

1. Selecione **Salvar rascunho**.

1. Selecione **Preço e disponibilidade** no painel esquerdo.

1. Adicione detalhes de preço e disponibilidade.

   :::image type="content" source="~/assets/images/first-party-license-mgt/pricing-availability.png" alt-text="As capturas de tela mostram a página de preços e disponibilidade para adicionar a oferta de SaaS para seu aplicativo.":::

1. Selecione **Salvar rascunho**.

1. Selecione **Visão geral** do plano na parte superior da página para ir para a página de listagem que mostra todos os planos que você criou para essa oferta.

   :::image type="content" source="~/assets/images/first-party-license-mgt/list-of-plans-created.png" alt-text="As capturas de tela mostram a página de listagem de planos com a ID do serviço, o modelo de preços, a disponibilidade, o status e a ação.":::

1. Copie a ID de serviço do plano que você criou para integrar-se à API de Direitos de Uso do Microsoft Graph.

### <a name="update-your-teams-app"></a>Atualizar seu aplicativo Teams

Atualize seu aplicativo Teams para mapear para a funcionalidade paga e [mapear seu aplicativo Teams](https://aka.ms/TMTG) para sua oferta e publicar.

### <a name="post-purchase"></a>Pós-compra

1. Após a ativação, o cliente é redirecionado da página de aterrissagem para o Gerenciamento de Licenças do Teams.

1. Após a conclusão bem-sucedida da compra da assinatura, o cliente é redirecionado para a página de aterrissagem do aplicativo para a ativação da assinatura. Essa é a experiência existente para o usuário comprar aplicativos [monetizados no Teams](https://aka.ms/TMTG).

1. Depois que o cliente ativa a compra da assinatura na página de aterrissagem, o cliente é redirecionado para a página de assinaturas no Teams por meio de um link de [URL](https://teams.microsoft.com/_#/subscriptionManagement) de redirecionamento ou botão que o cliente seleciona na página de aterrissagem do editor.

### <a name="integrate-with-graph-usage-right-api"></a>Integrar com a API de Uso correto do Graph

Integre-se à API de Direito de Uso do Graph para gerenciar permissões de usuário no momento da inicialização do aplicativo por um cliente que tenha uma licença de compra. Você precisa determinar as permissões do usuário para o aplicativo com uma chamada do Graph para a API de Direitos de Uso.

Você pode chamar APIs do Graph para determinar se o usuário conectado no momento com uma assinatura válida do plano tem acesso ao seu aplicativo. Para chamar a API UsageRight do Graph para verificar as permissões do usuário, siga as etapas:

1. Obter o token OBO do usuário: [obter acesso em nome de um usuário – Microsoft Graph | Microsoft Docs](/graph/auth-v2-user).

1. Chamar o Graph para obter a ID de objeto do usuário: [use o Microsoft API do Graph – Microsoft Graph | Microsoft Docs](/graph/use-the-api).

1. Chamar a API UsageRights para determinar que o usuário tem Licença para o plano [Listar usageRights - Microsoft Graph beta | Microsoft Docs](/graph/api/user-list-usagerights?view=graph-rest-beta&tabs=http&preserve-view=true).

   > [!NOTE]
   > Você precisa ter permissões mínimas `User.Read` para chamar UsageRights.
   > A API UsageRights está atualmente na versão beta. Depois que a versão for atualizada para v1, os usuários do ISV deverão atualizar da versão beta para v1.

### <a name="check-license-usage-in-partner-center-analytics"></a>Verificar o uso da licença na análise do Partner Center

1. Acesse o [Partner Center](https://partner.microsoft.com/).
1. No painel esquerdo, vá para o **Marketplace Comercial > Analisar > Licenciamento**.
1. Selecione **Plano e Locatário** no widget de relatório para ver o uso mensal.

## <a name="build-a-landing-page-for-subscription-management"></a>Criar uma página de aterrissagem para gerenciamento de assinaturas

Quando alguém terminar de comprar um plano de assinatura para seu aplicativo na loja do Teams, o marketplace comercial o direcionará para sua página inicial, onde poderá gerenciar a assinatura (por exemplo, atribuir uma licença a um usuário específico em sua organização).

Selecione **Não, prefiro gerenciar as licenças de cliente nesses** casos.

Para obter instruções completas, [criar a página de aterrissagem para sua oferta de SaaS](/azure/marketplace/azure-ad-transactable-saas-landing-page).

Quando alguém terminar de comprar um plano de assinatura para seu aplicativo e quiser permanecer no Teams, sem direcioná-lo para sua página de aterrissagem **, selecione Sim,** gostaria que a Microsoft gerenciando licenças de cliente em meu nome.

Para obter mais informações, consulte [gerenciamento de licenças de terceiros](/platform/concepts/deploy-and-publish/appsource/prepare/first-party-license-management).

### <a name="best-practices-for-landing-pages"></a>Práticas recomendadas para páginas de aterrissagem

Considere as seguintes abordagens ao criar uma página de aterrissagem para o aplicativo do Teams que você está monetizando. Consulte uma página de aterrissagem de exemplo na [experiência de compra do usuário final](#end-user-purchasing-experience).

* Os usuários devem ser capazes de entrar em sua página de aterrissagem com as mesmas credenciais do Azure AD usadas para comprar a assinatura. Para obter mais informações, confira [ofertas de SaaS transacionáveis e do Azure AD no marketplace comercial](/azure/marketplace/azure-ad-saas).
* Permitir que os usuários tomem as seguintes ações em sua página de aterrissagem. Não se esqueça de considerar o que é apropriado para a função e as permissões de um usuário. Por exemplo, você pode permitir que apenas administradores da assinatura pesquisem usuários):
  * Pesquisar usuários em sua organização usando email ou outra forma de identidade.
  * Consultar usuários aos que podem atribuir licenças em uma lista.
  * Atribuir licenças a um ou vários usuários ao mesmo tempo.
  * Atribuir e gerenciar diferentes tipos de licenças (se disponível).
  * Validar se uma licença já estiver atribuída a outro usuário.
  * Cancelar a assinatura.
* Forneça uma introdução sobre como usar seu aplicativo.
* Adicione maneiras de obter suporte, como perguntas frequentes, base de dados de conhecimento ou email de contato.
* Forneça um link que facilita o acesso do assinante à página de aterrissagem. Por exemplo, inclua esse link na guia **Sobre** do seu aplicativo.

## <a name="create-your-saas-offer"></a>Criar sua oferta de SaaS

Depois de integrar as APIs de atendimento de Saas e criar sua página de aterrissagem onde os usuários podem gerenciar suas assinaturas, é hora de criar, testar e publicar oficialmente sua oferta de SaaS transacionável.

### <a name="create-the-offer"></a>Criar a oferta

Consulte [criar uma oferta de SaaS](/azure/marketplace/create-new-saas-offer) para obter instruções completas sobre como fazer isso na Central de Parceiros. As etapas a seguir descrevem o que fazer em alto nível.

1. Crie uma conta na [Central de Parceiros](https://partner.microsoft.com/) se você não tiver uma.

1. Configure os planos de assinatura, detalhes de preços e muito mais para sua oferta de SaaS transacionável. Em particular, certifique-se de concluir as seguintes etapas:

    * Em **Detalhes da instalação**, selecione a opção **Sim** para especificar que você está vendendo a oferta por meio da Microsoft.

    * Em integração do **Microsoft 365**, adicione o link AppSource à listagem do aplicativo. Esta etapa garante que as pessoas possam comprar seus planos de assinatura no AppSource, além do Teams.

1. Armazene seu editor e ofereça IDs. (Você precisa deles mais tarde para vincular a oferta ao seu aplicativo no Portal do Desenvolvedor.)

1. Publique sua oferta no marketplace comercial.

### <a name="test-the-offer"></a>Testar a oferta

Recomendamos que você verifique a experiência de compra de ponta a ponta antes de publicar a sua oferta de SaaS. Você pode verificar criando uma oferta separada apenas para teste. Para obter informações completas, consulte [Visão geral da oferta de teste](/azure/marketplace/plan-saas-offer#test-offer), [crie uma oferta de teste](/azure/marketplace/create-saas-dev-test-offer) e [visualize sua oferta](/azure/marketplace/test-publish-saas-offer).

> [!IMPORTANT]
> Você pode testar uma transação de ponta a ponta no Teams usando o recurso [Teste de visualização para aplicativos monetizados](Test-preview-for-monetized-apps.md). Para ofertas dinâmicas, você deve concluir o processo de validação da loja de aplicativos.

Do ponto de Teams, esses testes devem verificar se o número de licenças e atribuições corresponderá ao que está no centro de administração Teams quando os usuários:

* Ativarem e configurarem o plano de assinatura na página inicial.
* Atribuírem, removerem ou reatribuírem licenças a si mesmos ou a outras pessoas.
* Cancelarem ou renovarem sua assinatura.

### <a name="publish-the-offer"></a>Publicar a oferta

Depois de concluir o teste, [publique sua oferta ao vivo](/azure/marketplace/test-publish-saas-offer#publish-your-offer-live).

## <a name="configure-your-app-for-the-saas-offer"></a>Configurar seu aplicativo para a oferta de SaaS

Você publicou sua oferta SaaS, mas ainda deve vinculá-la ao seu aplicativo do Teams para que os usuários vejam seus planos de assinatura na loja do Teams.

1. Vá para o [Portal do Desenvolvedor e](https://dev.teams.microsoft.com/) selecione **Aplicativos**.
1. Na página **Aplicativos**, selecione o aplicativo ao que você está vinculando a oferta SaaS.
1. Vá até a página **Planos e preços** e especifique seu editor e IDs de oferta. (Você pode encontrar essas IDs na Central de Parceiros se não as tiver prontamente disponíveis.)
1. Selecione **Exibir** para visualizar os planos de assinatura da oferta de SaaS.
1. Se tudo estiver correto, selecione **Salvar**.

   A propriedade `subscriptionOffer` é adicionada ao [manifesto do aplicativo](~/resources/schema/manifest-schema-dev-preview.md#subscriptionoffer).

   ```json
      "subscriptionOffer": {
        "offerId": "publisherId.offerId"  
        }
   ```

## <a name="publish-your-app"></a>Publicar seu aplicativo

Você criou sua oferta de SaaS e a vinculou ao seu aplicativo Teams, agora é hora de publicar seu aplicativo na loja do Teams. Para obter instruções completas, confira [Publicar seu aplicativo na loja do Teams](~/concepts/deploy-and-publish/appsource/publish.md).

> [!IMPORTANT]
>
> * Mesmo que seu aplicativo já esteja listado na loja do Teams, você ainda deve passar pelo processo de validação da loja novamente para incluir sua oferta SaaS.
> * As ofertas de taxa fixa criadas sem a ID da oferta e a ID do editor no manifesto do aplicativo devem ser atualizadas e reenviadas para validação.

Depois de publicado, os usuários verão uma opção **Comprar uma assinatura** na caixa de diálogo de detalhes do aplicativo quando tentarem adicionar seu aplicativo ao Teams.

## <a name="end-user-purchasing-experience"></a>Experiência de compra do usuário final

O exemplo a seguir mostra como os usuários podem comprar planos de assinatura para um aplicativo Teams fictício chamado *Recloud*.

1. Na loja do Teams, encontre e selecione o aplicativo *Recloud*.

1. Na caixa de diálogo de detalhes do aplicativo, selecione **Comprar uma assinatura**.

    :::image type="content" source="~/assets/images/saas-offer/buysubscriptionplan.png" alt-text="Comprando a assinatura do aplicativo selecionado.":::

1. Selecione seu país para ver planos de assinatura para seu local.

1. Na caixa **Escolha um plano de assinatura**, escolha o plano desejado e selecione **Check-out**. (Observação: os planos privados ficam visíveis apenas para os usuários nas organizações às as que você está fornecendo a oferta. Esses planos são indicados com um **ícone de oferta** :::image type="icon" source="~/assets/icons/special-icon.png"::: especial.)

    :::image type="content" source="~/assets/images/saas-offer/choosingsubscriptionplan.png" alt-text="Selecionando o plano de assinatura apropriado.":::

1. Na caixa **Check-out**, forneça as informações necessárias e selecione **Fazer pedido**.

    :::image type="content" source="~/assets/images/saas-offer/placesubscriptionorder.png" alt-text="Inserindo o pedido de assinatura.":::

1. Quando solicitado, selecione **Configurar agora** para configurar sua assinatura.

    :::image type="content" source="~/assets/images/saas-offer/saas-offer-set-up.png" alt-text="Configurando a assinatura.":::

1. Gerencie seu plano de assinatura por meio do site do *Recloud* (também conhecido como uma [página de aterrissagem](#build-a-landing-page-for-subscription-management)).

    :::image type="content" source="~/assets/images/saas-offer/subscriptionlicenses.png" alt-text="Configurando licenças de usuário.":::

## <a name="admin-purchasing-experience"></a>Experiência de compra do administrador

Os administradores podem comprar planos de assinatura de aplicativo [centro de administração do Teams](/MicrosoftTeams/purchase-third-party-apps).

## <a name="remove-a-saas-offer-from-your-app"></a>Remover uma oferta de SaaS do seu aplicativo

Se você desvincular uma oferta SaaS incluída na listagem da loja Teams, você deve republicar seu aplicativo para ver a alteração na loja.

1. Vá para o [Portal do Desenvolvedor e](https://dev.teams.microsoft.com/) selecione **Aplicativos**.
1. Na página **Aplicativos**, selecione o aplicativo de onde você está removendo a oferta.
1. Vá para a página **Planos e preços** e selecione **Reverter**.
1. Depois que a oferta é desvinculada, faça o seguinte para atualizar a listagem da loja:
   1. Selecione **Distribuir > Publicar no repositório do Teams**.
   1. Selecione **Abrir a Central de Parceiros** para iniciar o processo de publicação do aplicativo sem a oferta.

## <a name="see-also"></a>Confira também

* [Mantendo e dando suporte ao aplicativo publicado](../post-publish/overview.md)
* [Diretrizes de validação para aplicativos vinculados à oferta de SaaS](teams-store-validation-guidelines.md#apps-linked-to-saas-offer)
