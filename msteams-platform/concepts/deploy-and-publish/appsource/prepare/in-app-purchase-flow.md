---
title: Fluxo de compra no aplicativo para monetização de aplicativos
description: Aprenda as tarefas e conceitos básicos necessários para implementar compras no aplicativo e funcionalidade de avaliação em aplicativos de equipes.
author: v-npaladugu
ms.author: surbhigupta
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: f404c80a8b5db61636e175ca6439b32938358cac
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073297"
---
# <a name="in-app-purchases"></a>Compras no aplicativo

O Microsoft Teams fornece APIs que você pode usar para implementar as compras no aplicativo para atualizar de aplicativos gratuitos para aplicativos pagos do Teams. A compra no aplicativo permite converter usuários de planos gratuitos para pagos diretamente de seu aplicativo.

## <a name="implement-in-app-purchases"></a>Implementar compras no aplicativo

Para oferecer uma experiência de compra no aplicativo aos usuários do seu aplicativo, verifique o seguinte:

* O aplicativo é construído na [biblioteca do SDK do cliente do Teams](https://github.com/OfficeDev/microsoft-teams-library-js).

* O aplicativo está habilitado com uma [oferta SaaS](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md) transacionável.

* O aplicativo está habilitado com [permissões RSC](#update-manifest).

* O aplicativo é invocado com a [`openPurchaseExperience` API](#purchase-experience-api).

A experiência de compra no aplicativo pode ser habilitada atualizando o arquivo `manifest.json` ou habilitando **Mostrar ofertas de compra no aplicativo** na seção **Permissões** do **Portal do desenvolvedor**.

### <a name="update-manifest"></a>Atualizar manifesto

Para habilitar a experiência de compra no aplicativo, atualize o arquivo `manifest.json` do aplicativo Teams adicionando as permissões RSC. Ele permite que os usuários do seu aplicativo atualizem para uma versão paga do seu aplicativo e comecem a usar novas funcionalidades. A atualização para o manifesto do aplicativo é a seguinte:

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

### <a name="purchase-experience-api"></a>API de experiência de compra

Para acionar a compra no aplicativo para o aplicativo, invoque a API `openPurchaseExperience` do seu aplicativo da web.

Veja a seguir um exemplo de como chamar a API do aplicativo:

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

## <a name="end-user-in-app-purchasing-experience"></a>Experiência de compra no aplicativo do usuário final

O exemplo a seguir mostra os usuários comprarem planos de assinatura para um aplicativo fictício do Teams chamado *Tarefas da Contoso para Teams*:

1. Na **Repositório** do Teams, localize e selecione o aplicativo.

1. Na caixa de diálogo de detalhes do aplicativo, selecione **Comprar uma assinatura** ou **Adicionar para mim**.

    :::image type="content" source="~/assets/images/saas-offer/buysubscriptionplancontoso.png" alt-text="Compre a assinatura do aplicativo selecionado." border="true":::

1. **Adicionar para mim** oferece uma versão de avaliação gratuita do aplicativo e, posteriormente, **Atualizá-lo** para uma versão paga.

    :::image type="content" source="~/assets/images/saas-offer/upgradeapp.png" alt-text="Fazendo upgrade para a assinatura do aplicativo selecionado." lightbox="../../../../assets/images/saas-offer/upgradeapp.png" border="true":::

1. Na caixa de diálogo **Escolher um plano de assinatura**, escolha o plano e selecione **Checkout**.

    :::image type="content" source="~/assets/images/saas-offer/choosingsubscriptionplancontoso.png" alt-text="Selecionando o plano de assinatura apropriado." lightbox="../../../../assets/images/saas-offer/choosingsubscriptionplancontoso.png" border="true":::

1. Conclua a transação e selecione **Configurar agora para configurar sua assinatura**.

    :::image type="content" source="~/assets/images/saas-offer/saas-offer-configure-now.png" alt-text="Configurando a assinatura." lightbox="../../../../assets/images/saas-offer/saas-offer-configure-now.png" border="true":::

    :::image type="content" source="~/assets/images/saas-offer/getstarted.png" alt-text="Página de destino da assinatura." lightbox="../../../../assets/images/saas-offer/getstarted.png" border="true":::

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Teste de visualização para aplicativos monetizados](~/concepts/deploy-and-publish/appsource/prepare/Test-preview-for-monetized-apps.md)

## <a name="see-also"></a>Confira também

* [Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
* [Criar uma oferta de Software como Serviço (SaaS)](include-saas-offer.md#create-your-saas-offer)
