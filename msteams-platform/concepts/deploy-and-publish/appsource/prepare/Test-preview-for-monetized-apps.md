---
title: Teste de visualização para aplicativos monetizados
author: v-ypalikila
description: Crie e teste ofertas de Visualização de SaaS para o aplicativo Teams antes de enviar a oferta ao vivo. Crie uma ID de oferta de visualização, configure seu aplicativo com a ID da oferta de visualização e sideload.
ms.topic: conceptual
ms.author: v-ypalikila
ms.localizationpriority: high
ms.openlocfilehash: 98b9876a93fe6040cf66a16475fe7fdacf98a520
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100788"
---
# <a name="test-preview-for-monetized-apps"></a>Teste de visualização para aplicativos monetizados

Você pode criar uma oferta de Software como Serviço (SaaS) e testar a experiência de compra de ponta a ponta para seus aplicativos monetizados no Teams. Os usuários adicionados como audiência de visualização para o aplicativo do Teams podem revisar sua oferta SaaS antes de publicar.

## <a name="create-a-preview-offer-id"></a>Criar uma ID da oferta de visualização

Você pode gerar a ID da oferta de visualização a partir do link de **visualização do AppSource** no Partner Center. Verifique se a oferta SaaS está na fase de criação de visualização. Para gerar a ID da oferta de visualização:

1. Vá para o [Partner Center](https://go.microsoft.com/fwlink/?linkid=2166002) e entre usando suas credenciais de desenvolvedor.
1. Selecione **Ofertas do Marketplace**.
1. Selecione a oferta SaaS que você deseja visualizar.
1. Adicione uma [audiência de visualização](/azure/marketplace/create-new-saas-offer-preview) para sua oferta SaaS.
1. Selecione o link **Visualização do AppSource** em **Go Live** para encontrar a ID da oferta de visualização na barra de endereços do navegador com o formato *publisherId.offerId-preview*.

    :::image type="content" source="../../../../assets/images/apps-in-meetings/publish-status-publisher-signoff.png" alt-text="ID da oferta de visualização" :::

1. Copie a ID da oferta de visualização da barra de endereços do navegador.

      :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-monetized-apps-preview-offer-id.png" alt-text="ID da oferta de visualização" :::

    > [!NOTE]
    > Unlike a public offer ID, the Preview offer ID can be recognized with the *-preview* suffix. For example, **publisherId.offerId-preview**.

## <a name="configure-your-app-with-the-preview-offer-id"></a>Configurar seu aplicativo com a ID da oferta de visualização

Antes de começar, entre no **Portal do Desenvolvedor** usando uma conta de desenvolvedor com **audiência de visualização** para que os usuários vejam seus planos de assinatura no repositório do Teams.

After you've generated your Preview offer ID, link the offer ID to your Teams app. To link the offer ID:

1. Acesse o [Portal do Desenvolvedor](https://dev.teams.microsoft.com/) e entre usando suas credenciais de desenvolvedor.
1. Selecione **Aplicativos** no painel esquerdo.
1. Selecione o aplicativo para vincular a oferta SaaS.
1. Selecione **Planos e preços** e insira a **ID do Publisher** e a **ID da Oferta**.  
  Verifique se a ID da oferta contém o sufixo *-preview*.
1. Selecione **Exibir** para visualizar seus planos de assinatura.
1. Revise os planos listados em **Assinatura de Aplicativos** e selecione **Salvar**.

    :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-add-offer-id.png" alt-text="adicionar id da oferta" :::

A propriedade subscriptionOffer é adicionada ao manifesto do aplicativo.

```json
"subscriptionOffer": {
     "offerId": "publisherId.offerId-preview"  
     }
```

>[!NOTE]
> Verifique se o rótulo *Oferta de visualização* ao lado da **Assinatura de aplicativos** para confirmar se a oferta é uma Oferta de Visualização.

## <a name="sideload-the-app-to-teams"></a>Fazer sideload do aplicativo para o Teams

Depois de configurar seu aplicativo com a ID da Oferta de visualização, crie um pacote de aplicativo atualizado e carregue-o no Teams para testar a experiência de compra de ponta a ponta. Para obter mais informações, consulte [Carregue seu aplicativo no Microsoft Teams](../../apps-upload.md). Você também pode selecionar **Visualizar no Teams** no Portal do Desenvolvedor para Teams para iniciar seu aplicativo rapidamente no cliente do Teams.

Se a Oferta de visualização for especificada no manifesto do aplicativo e a audiência de visualização for definida no Partner Center para a oferta, o usuário poderá ver o botão **Comprar uma assinatura**.

:::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-buy-subscription.png" alt-text="comprar uma assinatura":::

### <a name="error-scenarios"></a>Cenários de erro

* Se a ID da oferta for especificada, mas o usuário não fizer parte da **Audiência de visualização** definida no Partner Center, o botão **Comprar uma assinatura** não estará habilitado e o aplicativo mostrará a seguinte mensagem de aviso para o usuário:

  Nenhum plano encontrado com **-preview**. Certifique-se de estar na audiência de visualização.

  :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-no-preview-audience.png" alt-text="nenhuma audiência de visualização" :::

* Se a ID da oferta especificada no manifesto do aplicativo não for uma Oferta de Visualização, o aplicativo mostrará a seguinte mensagem de aviso para o usuário e o sideload será desabilitado:
  
  Isso não é uma oferta de visualização. Certifique-se de anexar **-preview** à ID da Oferta.

  :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-no-preview-offer-id.png" alt-text="sem visualização" :::

## <a name="see-also"></a>Confira também

* [Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](include-saas-offer.md)
* [Criar uma oferta de Software como Serviço (SaaS)](include-saas-offer.md#create-your-saas-offer)
* [Adicionar uma audiência de visualização para uma oferta SaaS](/azure/marketplace/create-new-saas-offer-preview)
* [Fase de criação de visualização](/azure/marketplace/review-publish-offer)
* [Revisar e publicar uma oferta para o marketplace comercial](/azure/marketplace/review-publish-offer#validation-and-publishing-steps)
