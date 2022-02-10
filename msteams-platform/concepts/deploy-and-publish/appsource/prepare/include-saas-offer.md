---
title: Incluir uma oferta SaaS com seu aplicativo
description: Saiba como monetizar seu aplicativo Microsoft Teams com planos de assinatura.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: how-to
ms.localizationpriority: medium
ms.openlocfilehash: 837c311bf777b337187dbc54555b5268082a103f
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62517985"
---
# <a name="include-a-saas-offer-with-your-microsoft-teams-app"></a>Incluir uma oferta SaaS com seu Microsoft Teams app

:::row:::
   :::column span="3":::

Com uma oferta de Software como serviço (SaaS) transacionável, você pode monetizar seu aplicativo Teams por meio da venda de planos de assinatura diretamente da listagem da Teams store. Por exemplo, digamos que você tenha um aplicativo gratuito que qualquer pessoa pode obter na loja. Agora você pode oferecer planos premium e empresariais para usuários que querem mais recursos.

Aqui está uma ideia geral de como monetizar seu aplicativo:

1.  [Planeje sua oferta SaaS](#plan-your-saas-offer).

1.  [Integre-se às APIs de Atendimento saas](#integrate-with-the-saas-fulfillment-apis).

1.  [Crie uma página inicial para gerenciamento de assinatura](#build-a-landing-page-for-subscription-management).

1.  [Crie sua oferta SaaS](#create-your-saas-offer).

1.  [Configure seu aplicativo para a oferta SaaS](#configure-your-app-for-the-saas-offer).

1.  [Publique seu aplicativo no Teams store](#publish-your-app).

   :::column-end:::
   :::column span="1":::
   
:::image type="content" source="~/assets/images/saas-offer/saas-offer-diagram.png" alt-text="Diagrama mostrando o processo de como incluir uma oferta SaaS com seu Teams app." border="false":::

   :::column-end:::
:::row-end:::

## <a name="plan-your-saas-offer"></a>Planejar sua oferta SaaS

Para obter orientações abrangentes, [consulte como planejar uma oferta SaaS para o marketplace comercial da Microsoft](/azure/marketplace/plan-saas-offer).

Ao planejar como monetizar seu aplicativo Teams, veja algumas coisas a considerar:

* Decida o modelo de assinatura. Uma oferta saaS transactável pode incluir vários planos de assinatura. Os planos de assinatura pública disponíveis para qualquer pessoa são mais comuns, mas você também pode querer direcionar clientes específicos com ofertas apenas para eles. Para obter mais informações, consulte [ofertas privadas no marketplace comercial da Microsoft](/azure/marketplace/private-offers).
* Leia sobre a opção [*Vender por meio da Microsoft*](/azure/marketplace/plan-saas-offer#listing-options) para sua oferta saaS, que é necessária se você quiser que os usuários comprem planos de assinatura para seu aplicativo diretamente por meio da Teams store.
* Saiba como [Azure Active Directory SSO (login único)](/azure/marketplace/azure-ad-saas) ajuda seus clientes a comprar e gerenciar assinaturas. (Microsoft Azure Active Directory (Azure AD) SSO é necessário para Teams aplicativos com ofertas saaS.)
* Entenda que você é responsável pelo gerenciamento e pagamento da infraestrutura necessária para dar suporte ao uso da oferta saaS dos seus clientes.
* Planejar para celular. Para evitar violar políticas de armazenamento de aplicativos de terceiros, seu aplicativo não pode incluir links que permitem que os usuários comprem planos de assinatura em dispositivos móveis. No entanto, você ainda pode indicar se seu aplicativo tem recursos que exigem um plano de assinatura. Para obter mais informações, consulte as políticas de [certificação do marketplace comercial relacionadas](/legal/marketplace/certification-policies#114048-mobile-experience).

## <a name="integrate-with-the-saas-fulfillment-apis"></a>Integrar-se às APIs de Atendimento saas

A integração com as APIs de Atendimento saas é necessária para monetizar seu Teams app. Essas APIs ajudam você a gerenciar o ciclo de vida de um plano de assinatura depois que ele é comprado por um usuário.

Para obter instruções completas e referência à API, consulte a documentação das [APIs de Atendimento saas](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-apis). Em geral, você implementará as etapas a seguir usando as APIs depois que uma assinatura for comprada:

1. Receba um [*token de identificação de compra*](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-life-cycle#purchased-but-not-yet-activated-pendingfulfillmentstart) por meio da URL para sua página inicial.

1. Use o token para recuperar detalhes da assinatura.

1. Notifique o marketplace comercial de que a assinatura está ativada.

### <a name="best-practices-for-implementing-subscription-management"></a>Práticas recomendadas para implementar o gerenciamento de assinaturas

* Com as ofertas de SaaS transacíveis para aplicativos Teams, os planos de assinatura (licenças) devem ser atribuídos a usuários individuais, em vez de grupos ou a uma organização inteira.
* Quando os usuários receberem um plano de assinatura, notifique-os por meio de um bot Teams ou email. Na mensagem, inclua informações sobre como adicionar o aplicativo Teams e começar.
* Suporte à ideia de vários administradores. Em outras palavras, vários usuários na mesma organização podem comprar e gerenciar suas próprias assinaturas.

## <a name="build-a-landing-page-for-subscription-management"></a>Criar uma página inicial para gerenciamento de assinaturas 

Quando alguém terminar de comprar um plano de assinatura para seu aplicativo na loja Teams, o marketplace comercial o direcionará para sua página inicial, onde poderá gerenciar a assinatura (por exemplo, atribuir uma licença a um usuário específico em sua organização).

Para obter instruções completas, [consulte build the landing page for your SaaS offer](/azure/marketplace/azure-ad-transactable-saas-landing-page).

### <a name="best-practices-for-landing-pages"></a>Práticas recomendadas para páginas de aterrissagem

Considere as seguintes abordagens ao criar uma página de aterrissagem para o Teams aplicativo que você está monetizando. Consulte uma página de aterrissagem de exemplo na [experiência de compra do usuário final](#end-user-purchasing-experience).

* Os usuários devem poder fazer logoff na página inicial com as mesmas credenciais Microsoft Azure Active Directory (Azure AD) usadas para comprar a assinatura. Para obter mais informações, [consulte Microsoft Azure Active Directory (Azure AD) e ofertas de SaaS transacíveis no marketplace comercial](/azure/marketplace/azure-ad-saas).
* Permitir que os usuários tomem as seguintes ações em sua página de aterrissagem. Não se esqueça de considerar o que é apropriado para a função e as permissões de um usuário (por exemplo, talvez você queira permitir que apenas os administradores de assinatura pesquisem por usuários):
  * Pesquise usuários em sua organização usando email ou outra forma de identidade.
  * Consulte usuários aos que podem atribuir licenças em uma lista.
  * Atribua licenças a um ou vários usuários ao mesmo tempo.
  * Atribua e gerencie diferentes tipos de licenças (se disponível).
  * Valide se uma licença já estiver atribuída a outro usuário.
  * Cancele sua assinatura.
* Forneça uma introdução sobre como usar seu aplicativo.
* Adicione maneiras de obter suporte, como perguntas frequentes, base de dados de conhecimento ou email de contato.
* Forneça um link que facilita o retorno do assinante à página inicial. Por exemplo, inclua esse link na guia Sobre **do** seu aplicativo.

## <a name="create-your-saas-offer"></a>Criar sua oferta SaaS

Depois de integrar as APIs de Atendimento saas e criar sua página inicial onde os usuários podem gerenciar suas assinaturas, é hora de criar, testar e publicar oficialmente sua oferta de SaaS transacível.

> [!IMPORTANT]
> Teams atualmente suporta apenas **o** modelo de preços por usuário (usuário/mês e usuário/ano) para ofertas saaS. Para obter mais informações, consulte [Modelos de preços saaS](/azure/marketplace/plan-saas-offer#saas-pricing-models).

### <a name="create-the-offer"></a>Criar a oferta

Consulte [criar uma oferta SaaS para](/azure/marketplace/create-new-saas-offer) obter instruções completas sobre como fazer isso no Partner Center. As etapas a seguir descrevem o que fazer em alto nível.

1.  Crie uma [conta do Partner Center](https://partner.microsoft.com/) se você não tiver uma.

1.  Configure os planos de assinatura, detalhes de preços e muito mais para sua oferta de SaaS transactável. Em particular, certifique-se de concluir as seguintes etapas:

    * Em **Detalhes da Instalação**, selecione **a opção Sim** para especificar que você está vendendo a oferta por meio da Microsoft.
     
    * Em **Microsoft 365 integração**, adicione o link AppSource à listagem do aplicativo. Esta etapa garante que as pessoas possam comprar seus planos de assinatura no AppSource, além de Teams.

1. Armazene seu editor e ofereça IDs. (Você precisa deles mais tarde para vincular a oferta ao seu aplicativo no Portal do Desenvolvedor.)

1. Publique sua oferta no marketplace comercial.

### <a name="test-the-offer"></a>Testar a oferta

Recomendamos que você verifique a experiência de compra de ponta a ponta antes de publicar sua oferta saaS. Você pode fazer isso criando uma oferta separada apenas para teste. Para obter informações completas, consulte [Visão geral da](/azure/marketplace/plan-saas-offer#test-offer) oferta de teste, [crie uma oferta de teste](/azure/marketplace/create-saas-dev-test-offer) e [visualize sua oferta](/azure/marketplace/test-publish-saas-offer).

> [!IMPORTANT]
> Você pode testar uma transação de ponta a ponta no Teams até que seu aplicativo conclua a validação da loja. Para obter mais informações, consulte [Test preview for monetized apps](Test-preview-for-monetized-apps.md).

Do ponto de Teams, esses testes devem verificar se o número de licenças e atribuições corresponderá ao que está no centro de administração Teams quando os usuários:

* Ative e configure o plano de assinatura na página inicial.
* Atribuir, remover ou reatribuir licenças a si mesmo ou a outras pessoas.
* Cancele ou renove sua assinatura.

### <a name="publish-the-offer"></a>Publicar a oferta

Depois de concluir o teste, [publique sua oferta ao vivo](/azure/marketplace/test-publish-saas-offer#publish-your-offer-live).

## <a name="configure-your-app-for-the-saas-offer"></a>Configurar seu aplicativo para a oferta saaS

Você publicou sua oferta saaS, mas ainda deve vinculá-la ao seu aplicativo Teams para que os usuários vejam seus planos de assinatura na Teams store.

1. Vá para o [Portal do Desenvolvedor e](https://dev.teams.microsoft.com/) selecione **Aplicativos**.
1. Na página **Aplicativos** , selecione o aplicativo ao que você está vinculando a oferta SaaS.
1. Vá até a **página Planos e preços** e especifique seu editor e IDs de oferta. (Você pode encontrar essas IDs no Partner Center se não as tiver prontamente disponíveis.)
1. Selecione **Exibir** para visualizar os planos de assinatura da oferta SaaS.
1. Se tudo estiver bem, selecione **Salvar**.

   A `subscriptionOffer` propriedade é adicionada ao manifesto [do aplicativo](~/resources/schema/manifest-schema-dev-preview.md#subscriptionoffer).

   ```json
      "subscriptionOffer": {
        "offerId": "publisherId.offerId"  
        }
   ```

## <a name="publish-your-app"></a>Publicar seu aplicativo

Você criou sua oferta saaS e a Teams seu aplicativo de Teams , agora é hora de publicar seu aplicativo no Teams store. Para obter instruções completas, [consulte publish your app to the Teams store](~/concepts/deploy-and-publish/appsource/publish.md).

> [!IMPORTANT]
> Mesmo que seu aplicativo já esteja listado na loja Teams, você ainda deve passar pelo processo de validação da loja novamente para incluir sua oferta saaS.

Depois de publicado, os usuários verão uma **opção Comprar** uma assinatura na caixa de diálogo detalhes do aplicativo quando tentarem adicionar seu aplicativo Teams.

## <a name="end-user-purchasing-experience"></a>Experiência de compra do usuário final

O exemplo a seguir mostra como os usuários podem comprar planos de assinatura para um aplicativo Teams fictício chamado *Recloud*.

1. Na Teams, encontre e selecione o *aplicativo Recloud*.

1. Na caixa de diálogo Detalhes do aplicativo, selecione **Comprar uma assinatura**.

    :::image type="content" source="~/assets/images/saas-offer/buysubscriptionplan.png" alt-text="Comprando a assinatura do aplicativo selecionado.":::

1. Selecione seu país para ver planos de assinatura para seu local.

1. Na caixa **de diálogo Escolher um plano de assinatura** , escolha o plano que deseja e selecione **Checkout**. (Observação: os planos privados ficam visíveis apenas para os usuários nas organizações às as que você está fornecendo a oferta. Esses planos são indicados com um **ícone de oferta** :::image type="icon" source="~/assets/icons/special-icon.png"::: especial.)

    :::image type="content" source="~/assets/images/saas-offer/choosingsubscriptionplan.png" alt-text="Selecionando o plano de assinatura apropriado.":::

1. Na caixa **de diálogo Checkout** , forneça todas as informações necessárias e selecione **Colocar ordem**.

    :::image type="content" source="~/assets/images/saas-offer/placesubscriptionorder.png" alt-text="Colocando o pedido de assinatura.":::

1. Quando solicitado, selecione **Configurar agora para** configurar sua assinatura.

    :::image type="content" source="~/assets/images/saas-offer/saas-offer-set-up.png" alt-text="Configurando a assinatura.":::

1. Gerencie seu plano de assinatura por meio do site *do Recloud* (também conhecido como uma [página de aterrissagem](#build-a-landing-page-for-subscription-management)).

    :::image type="content" source="~/assets/images/saas-offer/subscriptionlicenses.png" alt-text="Configurando licenças de usuário.":::

## <a name="admin-purchasing-experience"></a>Experiência de compra do administrador

Os administradores podem comprar planos de assinatura de aplicativo [no Teams de administração](/MicrosoftTeams/purchase-third-party-apps).

## <a name="remove-a-saas-offer-from-your-app"></a>Remover uma oferta SaaS do seu aplicativo

Se você desvincular uma oferta SaaS incluída na listagem da loja Teams, você deve republicar seu aplicativo para ver a alteração na loja.

1. Vá para o [Portal do Desenvolvedor e](https://dev.teams.microsoft.com/) selecione **Aplicativos**.
1. Na página **Aplicativos** , selecione o aplicativo de onde você está removendo a oferta.
1. Vá para a página **Planos e preços** e selecione **Reverter**.
1. Depois que a oferta é desvinculada, faça o seguinte para atualizar a listagem da loja:
   1. Selecione **Distribuir > Publicar no Teams store**.
   1. Selecione **Abrir o Partner Center** para iniciar o processo de publicação do aplicativo sem a oferta.

## <a name="see-also"></a>Confira também

[Mantendo e dando suporte ao aplicativo publicado](../post-publish/overview.md)
