---
title: Visualização de teste para aplicativos monetizados
author: v-ypalikila
description: Crie e teste as ofertas do SaaS Preview para Teams aplicativo antes de forçar a oferta ao vivo.
ms.topic: conceptual
ms.author: v-ypalikila
ms.localizationpriority: medium
keywords: aplicativos do teams SaaS oferecem versão prévia de teste de visualização monetizada saas
ms.openlocfilehash: 849dd2ecd79a4b43d6feb6ceaca599f371df1de1
ms.sourcegitcommit: 54f6690b559beedc330b971618e574d33d69e8a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62363403"
---
# <a name="test-preview-for-monetized-apps"></a>Visualização de teste para aplicativos monetizados

> [!NOTE]
> A visualização de teste para aplicativos monetizados está disponível apenas na [**visualização do desenvolvedor**](/microsoftteams/platform/resources/dev-preview/developer-preview-intro).

Você pode criar uma oferta software como serviço (SaaS) e testar a experiência de compra de ponta a ponta para seus aplicativos monetizados em Teams. Os usuários adicionados como audiência de visualização para o aplicativo Teams podem revisar sua oferta saaS antes de publicar.

## <a name="create-a-preview-offer-id"></a>Criar uma ID da oferta de visualização

Você pode gerar a ID da oferta de visualização a partir do link de **visualização do AppSource** no Partner Center. Verifique se a oferta saaS está na fase de criação de visualização. Para gerar a ID da oferta de visualização:

1. Vá para [o Partner Center](https://go.microsoft.com/fwlink/?linkid=2166002) e entre usando suas credenciais de desenvolvedor.
1. Selecione **Ofertas do Marketplace**.
1. Selecione a oferta SaaS que você deseja visualizar.
1. Adicione uma [audiência de visualização](/azure/marketplace/create-new-saas-offer-preview) para sua oferta saaS.
1. Selecione o link de visualização do **AppSource** em **Go Live** para encontrar a ID da oferta de visualização na barra de endereços do navegador com *o formato publisherId.offerId-preview* .

    :::image type="content" source="../../../../assets/images/apps-in-meetings/publish-status-publisher-signoff.png" alt-text="id da oferta de visualização" border="true" :::

1. Copie a ID da oferta de visualização da barra de endereços do navegador.

      :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-monetized-apps-preview-offer-id.png" alt-text="ID da oferta de visualização" border="true" :::

    > [!NOTE]
    > Ao contrário de uma ID de oferta pública, a ID da oferta de visualização pode ser reconhecida com *o sufixo -preview* . Por exemplo, **publisherId.offerId-preview**.

## <a name="configure-your-app-with-the-preview-offer-id"></a>Configurar seu aplicativo com a ID da oferta de visualização

Antes de começar, entre no **Portal** do Desenvolvedor usando uma conta de desenvolvedor com  audiência de visualização para que os usuários vejam seus planos de assinatura na Teams store.

Depois de gerar a ID da oferta de visualização, vincule a ID da oferta ao seu Teams app. Para vincular a ID da oferta:

1. Acesse o [Portal do Desenvolvedor](https://dev.teams.microsoft.com/) e entre usando suas credenciais de desenvolvedor.
1. Selecione **Aplicativos** no painel esquerdo.
1. Selecione o aplicativo para vincular a oferta SaaS.
1. Selecione **Planos e preços e** insira a **ID Publisher E** **ID da Oferta**.  
  Verifique se a ID da oferta contém *sufixo -preview* .
1. Selecione **Exibir para** visualizar seus planos de assinatura.
1. Revise os planos listados em **Assinatura de Aplicativos** e selecione **Salvar**.

    :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-add-offer-id.png" alt-text="adicionar id da oferta" :::

A propriedade subscriptionOffer é adicionada ao manifesto do aplicativo.

```json
"subscriptionOffer": {
     "offerId": "publisherId.offerId-preview"  
     }
```

>[!NOTE]
> Verifique a oferta de *visualização de rótulo* ao lado da assinatura **aplicativos** para confirmar se a oferta é uma Oferta de Visualização.

## <a name="sideload-the-app-to-teams"></a>Fazer sideload do aplicativo para Teams

Depois de configurar seu aplicativo com a ID da Oferta prévia, crie um pacote de aplicativo atualizado e carregue-o Teams para testar a experiência de compra de ponta a ponta. Para obter mais informações, [consulte Upload seu aplicativo em Microsoft Teams](../../apps-upload.md). Você também pode selecionar **Visualizar no Teams** no Portal do Desenvolvedor para Teams iniciar seu aplicativo rapidamente no cliente Teams usuário.

Se a oferta de visualização for especificada no manifesto do aplicativo e a audiência de visualização for definida no Partner center para a oferta, o usuário poderá ver o botão **Comprar uma** assinatura.

:::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-buy-subscription.png" alt-text="comprar uma assinatura" border="true":::

### <a name="error-scenarios"></a>Cenários de erro

* Se a ID da oferta for especificada, mas o usuário não faz parte do público visualização definido no Partner Center, o botão Comprar uma assinatura não está habilitado e o aplicativo mostra **a** seguinte mensagem de aviso para o usuário:

  Nenhum plano encontrado com **-preview**. Certifique-se de estar na audiência de visualização.

  :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-no-preview-audience.png" alt-text="nenhuma audiência pré-ivew" border="true" :::

* Se a ID da oferta especificada no manifesto do aplicativo não for uma oferta de Visualização, o aplicativo mostrará a seguinte mensagem de aviso para o usuário e o sideload será desabilitado:
  
  Isso não é uma oferta de visualização. Certifique-se de anexar **a -preview** à ID da Oferta.

  :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-no-preview-offer-id.png" alt-text="no -preview" border="true" :::

## <a name="see-also"></a>Confira também

* [Incluir uma oferta SaaS com seu Microsoft Teams app](include-saas-offer.md)
* [Criar uma oferta de Software como Serviço (SaaS)](include-saas-offer.md#create-your-saas-offer)
* [Adicionar uma audiência de visualização para uma oferta SaaS](/azure/marketplace/create-new-saas-offer-preview)
* [Fase de criação de visualização](/azure/marketplace/review-publish-offer)
* [Revisar e publicar uma oferta para o marketplace comercial](/azure/marketplace/review-publish-offer#validation-and-publishing-steps)
