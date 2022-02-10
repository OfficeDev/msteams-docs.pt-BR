---
title: Fluxo de compra no aplicativo para a monetização de aplicativos
description: Saiba as tarefas básicas e os conceitos necessários para implementar compras no aplicativo e funcionalidade de avaliação em aplicativos do teams.
author: v-npaladugu
ms.author: surbhigupta
ms.topic: how-to
localization_priority: Normal
ms.openlocfilehash: 90b1bf713e898a0f61c540e76ee5dde77603e70b
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518237"
---
# <a name="in-app-purchases"></a>Compras no aplicativo

Microsoft Teams fornecer APIs que você pode usar para implementar as compras no aplicativo para atualizar de aplicativos Teams gratuitos. A compra no aplicativo permite converter usuários de planos gratuitos para pagos diretamente de dentro de seu aplicativo.

> [!NOTE]
> As compras no aplicativo para Teams aplicativos estão disponíveis no momento apenas na [**visualização do desenvolvedor**](/microsoftteams/platform/resources/dev-preview/developer-preview-intro).

## <a name="implement-in-app-purchases"></a>Implementar compras no aplicativo

Para oferecer uma experiência de compra no aplicativo aos usuários do seu aplicativo, verifique o seguinte:

* O aplicativo é criado Teams [biblioteca SDK do cliente](https://github.com/OfficeDev/microsoft-teams-library-js).

* O aplicativo está habilitado com uma oferta [saaS transactável](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md).

* O aplicativo está habilitado com [permissões RSC](#update-manifest).

* O aplicativo é invocado com [`openPurchaseExperience` a API](#purchase-experience-api).

A experiência de compra no aplicativo pode ser habilitada atualizando o arquivo **manifest.json** ou habilitando Mostrar **ofertas** de compra no aplicativo na seção Permissões do seu **Portal do Desenvolvedor**.

### <a name="update-manifest"></a>Manifesto de atualização

Para habilitar a experiência de compra no aplicativo, atualize o arquivo **Teams app manifest.json** adicionando as permissões RSC. Ele permite que os usuários do aplicativo atualizem para uma versão paga do aplicativo e comecem a usar novas funcionalidades. A atualização do manifesto do aplicativo é a seguinte:

```json

"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "InAppPurchase.Allow.User",
                "type": "Delegated"
            }
        ]
    }
}
```

### <a name="purchase-experience-api"></a>API de Experiência de Compra

Para disparar a compra no aplicativo para o aplicativo, invoque a `openPurchaseExperience` API do seu aplicativo Web.

A seguir está um exemplo de chamada da API do aplicativo:

```json
<body> 
<div> 
<div class="sectionTitle">openPurchaseExperience</div> 
<button onclick="openPurchaseExperience()">openPurchaseExperience</button> 
</div> 
</body> 
<script> 
   function openPurchaseExperience() {
      microsoftTeams.initialize();
      let callbackcalled = false;
      microsoftTeams.monetization.openPurchaseExperience((e) => {
      console.log("callback is being called");
      callbackcalled = true;  
      if (!!e && typeof e !== "string") {
            e = JSON.stringify(e);
            alert(e);
        }
        return;
      });
      console.log("after callback: ",callbackcalled);
    } 
</script> 
```

## <a name="end-user-in-app-purchasing-experience"></a>Experiência de compra do usuário final no aplicativo

O exemplo a seguir mostra os usuários para comprar planos de assinatura para um aplicativo Teams fictício chamado *Tarefas contoso para Teams*:

1. Na Teams **Store**, encontre e selecione o aplicativo.

1. Na caixa de diálogo Detalhes do aplicativo, selecione **Comprar uma assinatura** ou **Adicionar para mim**. 

    :::image type="content" source="~/assets/images/saas-offer/buysubscriptionplancontoso.png" alt-text="Comprando a assinatura do aplicativo selecionado." border="true":::

    
1. **Adicionar para mim** oferece uma versão de avaliação gratuita do aplicativo e, **posteriormente, atualize-a** para uma versão paga.

    :::image type="content" source="~/assets/images/saas-offer/upgradeapp.png" alt-text="Atualizando para a assinatura do aplicativo selecionado." border="true":::

1. Na caixa **de diálogo Escolher um plano de assinatura** , escolha o plano e selecione **Checkout**.

    :::image type="content" source="~/assets/images/saas-offer/choosingsubscriptionplancontoso.png" alt-text="Selecionando o plano de assinatura apropriado." border="true":::

1. Conclua a transação e **selecione Configurar agora** para configurar sua assinatura.

    :::image type="content" source="~/assets/images/saas-offer/saas-offer-configure-now.png" alt-text="Configurando a assinatura." border="true":::

    :::image type="content" source="~/assets/images/saas-offer/getstarted.png" alt-text="Página inicial da assinatura." border="true":::

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Teste de visualização para aplicativos monetizados](~/concepts/deploy-and-publish/appsource/prepare/Test-preview-for-monetized-apps.md)

## <a name="see-also"></a>Confira também

* [Incluir uma oferta SaaS com seu Microsoft Teams app](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
* [Criar uma oferta de Software como Serviço (SaaS)](include-saas-offer.md#create-your-saas-offer)
