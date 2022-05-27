---
title: Incluir uma oferta SaaS com seu aplicativo
description: Saiba como monetizar seu aplicativo do Microsoft Teams com planos de assinatura.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: aa2aacb781909720bdb6a0bc27d593f9c73d11b0
ms.sourcegitcommit: a4b3b2fb265142155508f9b396609da1280df35d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65696456"
---
# <a name="include-a-saas-offer-with-your-microsoft-teams-app"></a>Incluir uma oferta SaaS com seu aplicativo

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

:::image type="content" source="~/assets/images/saas-offer/saas-offer-diagram.png" alt-text="Diagrama mostrando o processo de como incluir uma oferta de SaaS com seu aplicativo do Teams." border="false":::

   :::column-end:::
:::row-end:::

## <a name="plan-your-saas-offer"></a>Planejar a oferta de SaaS

Para obter diretrizes abrangentes, [consulte como planejar uma oferta de SaaS para o marketplace comercial da Microsoft](/azure/marketplace/plan-saas-offer).

Ao planejar como monetizar seu aplicativo do Teams, aqui estão algumas coisas a considerar:

* Decida o modelo de assinatura. Uma oferta SsaaS transacional pode incluir vários planos de assinatura. Os planos de assinatura pública disponíveis para qualquer pessoa são mais comuns, mas você também pode querer direcionar clientes específicos com ofertas apenas para eles. Para obter mais informações, consulte [ofertas privadas no marketplace comercial da Microsoft](/azure/marketplace/private-offers).
* Leia sobre a opção [*Vender por meio da Microsoft*](/azure/marketplace/plan-saas-offer#listing-options) para sua oferta do SaaS, que é necessária se você quiser que os usuários comprem planos de assinatura para seu aplicativo diretamente por meio da loja do Teams.
* Saiba como o [Azure Active Directory SSO (login único)](/azure/marketplace/azure-ad-saas) ajuda seus clientes a comprar e gerenciar assinaturas. (Microsoft Azure Active Directory (Azure AD) SSO é necessário para aplicativos do Teams com ofertas SaaS.)
* Entenda que você é responsável pelo gerenciamento e pagamento da infraestrutura necessária para dar suporte ao uso da oferta de SaaS dos seus clientes.
* Planeje para dispositivos móveis. Para evitar violar políticas de armazenamento de aplicativos de terceiros, seu aplicativo não pode incluir links que permitem que os usuários comprem planos de assinatura em dispositivos móveis. No entanto, você ainda pode indicar se seu aplicativo tem recursos que exigem um plano de assinatura. Para obter mais informações, consulte as [políticas de certificação do mercado comercial](/legal/marketplace/certification-policies#114048-mobile-experience) relacionadas.
* Atualmente, o Teams não oferece suporte a modelos de preços de taxa fixa. No entanto, você pode criar uma oferta transacionável de taxa fixa no Partner Center. Para obter mais informações, confira [as práticas recomendadas para vender uma oferta transacionável de taxa fixa](#best-practices-for-selling-a-flat-rate-transactable-offer).

## <a name="integrate-with-the-saas-fulfillment-apis"></a>Integrar-se às APIs de atendimento de Saas

A integração com as APIs de atendimento de SaaS é necessária para monetizar seu aplicativo do Teams. Essas APIs ajudam você a gerenciar o ciclo de vida de um plano de assinatura após ele ser comprado por um usuário.

Para obter instruções completas e referência à API, consulte a documentação das [APIs de atendimento de SaaS](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-apis). Em geral, você implementará as etapas a seguir usando as APIs após uma assinatura for comprada:

1. Receba um [*token de identificação de compra*](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-life-cycle#purchased-but-not-yet-activated-pendingfulfillmentstart) por meio da URL para sua página inicial.

1. Use o token para recuperar detalhes da assinatura.

1. Notifique o marketplace comercial de que a assinatura está ativada.

### <a name="best-practices-for-implementing-subscription-management"></a>Práticas recomendadas para implementar o gerenciamento de assinaturas

* Com as ofertas de SaaS transacionáveis para aplicativos do Teams, os planos de assinatura (licenças) devem ser atribuídos a usuários individuais, em vez de grupos ou a uma organização inteira.
* Quando os usuários receberem um plano de assinatura, notifique-os por meio de um bot Teams ou email. Na mensagem, inclua informações sobre como adicionar o aplicativo ao Teams e começar.
* Apoie a ideia de vários administradores. Em outras palavras, vários usuários na mesma organização podem comprar e gerenciar suas próprias assinaturas.

## <a name="build-a-landing-page-for-subscription-management"></a>Criar uma página de aterrissagem para gerenciamento de assinaturas

Quando alguém terminar de comprar um plano de assinatura para seu aplicativo na loja do Teams, o marketplace comercial o direcionará para sua página inicial, onde poderá gerenciar a assinatura (por exemplo, atribuir uma licença a um usuário específico em sua organização).

Para obter instruções completas, [criar a página de aterrissagem para sua oferta de SaaS](/azure/marketplace/azure-ad-transactable-saas-landing-page).

### <a name="best-practices-for-landing-pages"></a>Práticas recomendadas para páginas de aterrissagem

Considere as seguintes abordagens ao criar uma página de aterrissagem para o aplicativo do Teams que você está monetizando. Consulte uma página de aterrissagem de exemplo na [experiência de compra do usuário final](#end-user-purchasing-experience).

* Os usuários devem ser capazes de fazer logon em sua página de aterrissagem com as mesmas credenciais do Azure AD usadas para comprar a assinatura. Para obter mais informações, confira [ofertas de SaaS transacionáveis e do Azure AD no marketplace comercial](/azure/marketplace/azure-ad-saas).
* Permita que os usuários realizem as seguintes ações em sua página de aterrissagem. Não se esqueça de considerar o que é apropriado para a função e as permissões de um usuário (por exemplo, você pode permitir que apenas administradores de assinatura pesquisem usuários):
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

> [!IMPORTANT]
> O Teams atualmente suporta apenas o modelo de preços **por usuário** (usuário/mês e usuário/ano) para ofertas de SaaS. Para obter mais informações, consulte [Modelos de preços de SaaS](/azure/marketplace/plan-saas-offer#saas-pricing-models).

### <a name="create-the-offer"></a>Criar a oferta

Consulte [criar uma oferta de SaaS](/azure/marketplace/create-new-saas-offer) para obter instruções completas sobre como fazer isso na Central de Parceiros. As etapas a seguir descrevem o que fazer em alto nível.

1. Crie uma conta na [Central de Parceiros](https://partner.microsoft.com/) se você não tiver uma.

1. Configure os planos de assinatura, detalhes de preços e muito mais para sua oferta de SaaS transacionável. Em particular, certifique-se de concluir as seguintes etapas:

    * Em **Detalhes da instalação**, selecione a opção **Sim** para especificar que você está vendendo a oferta por meio da Microsoft.

    * Em integração do **Microsoft 365**, adicione o link AppSource à listagem do aplicativo. Esta etapa garante que as pessoas possam comprar seus planos de assinatura no AppSource, além do Teams.

1. Armazene seus IDs de editor e oferta. (Você precisará deles posteriormente para vincular a oferta ao seu aplicativo no Portal do desenvolvedor.)

1. Publique sua oferta no marketplace comercial.

### <a name="test-the-offer"></a>Testar a oferta

Recomendamos que você verifique a experiência de compra de ponta a ponta antes de publicar sua oferta de SaaS. Você pode fazer isso criando uma oferta separada apenas para teste. Para obter informações completas, consulte [Visão geral da oferta de teste](/azure/marketplace/plan-saas-offer#test-offer), [crie uma oferta de teste](/azure/marketplace/create-saas-dev-test-offer) e [visualize sua oferta](/azure/marketplace/test-publish-saas-offer).

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
> Mesmo que seu aplicativo já esteja listado na loja do Teams, você ainda deve passar pelo processo de validação da loja novamente para incluir sua oferta SaaS.

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

## <a name="best-practices-for-selling-a-flat-rate-transactable-offer"></a>Práticas recomendadas para vender uma oferta transacionável de taxa fixa

1. Crie sua [oferta de SaaS transacionável de taxa fixa](/azure/marketplace/plan-saas-offer) e [publique no AppSource](/azure/marketplace/test-publish-saas-offer).

1. Vincule sua [oferta de SaaS ao aplicativo Teams](/azure/marketplace/create-new-saas-offer) no Partner Center.

    > [!CAUTION]
    > Não adicione a ID da Oferta e Publisher ID ao manifesto do aplicativo. O aplicativo não passará no processo de envio da loja do Teams.

1. Crie uma mensagem no aplicativo em seu aplicativo do Teams informando que uma assinatura é necessária e forneça um hiperlink para sua oferta de SaaS no AppSource para promover sua oferta de taxa fixa.

   > [!NOTE]
   > Certifique-se de que nenhum link do mercado apareça em dispositivos móveis e tablets para cumprir as [políticas de lojas de aplicativos de terceiros](/legal/marketplace/certification-policies).

1. Envie seu aplicativo para validação.

1. Depois que o marketplace do Teams oferecer suporte a preços de taxa fixa, atualize o manifesto do aplicativo com a ID da oferta e a ID do editor e reenvie seu aplicativo para validação.

## <a name="see-also"></a>Confira também

[Mantendo e dando suporte ao aplicativo publicado](../post-publish/overview.md)
