---
title: Manter e dar suporte ao seu aplicativo publicado
description: Saiba como manter seu aplicativo Microsoft Teams publicado e o que fazer depois que sua loja for listada na loja do Teams e no AppSource. Analise o uso do aplicativo, publique atualizações, promova seu aplicativo, conclua a Certificação do Microsoft 365.
ms.topic: conceptual
ms.localizationpriority: high
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: f05613a54ea87660611bb4a4d66d2f88f9ee3b46
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100326"
---
# <a name="maintain-your-published-microsoft-teams-app"></a>Mantenha seu aplicativo Microsoft Teams publicado

Com seu aplicativo listado na loja do Microsoft Teams, comece a pensar em como você manterá o aplicativo no futuro e aumentará os downloads e o uso.

## <a name="analyze-app-usage"></a>Analisar o uso do aplicativo

Você pode acompanhar o uso do aplicativo no [Relatório de uso do Teams](/office/dev/store/teams-apps-usage) no Partner Center. As métricas incluem usuários ativos mensais, diários e semanais e gráficos de retenção e intensidade que permitem acompanhar a variação e a frequência de uso.

Os dados de aplicativos recém-publicados demoram cerca de uma semana para aparecer no relatório.

## <a name="publish-updates-to-your-app"></a>Publicar atualizações em seu aplicativo

> [!NOTE]
> A loja do Teams evoluiu:
>
> Anteriormente, os links eram copiados selecionando reticências no bloco do aplicativo. Com a experiência atualizada da loja do Teams, você acessará o mesmo na guia de detalhes dos aplicativos. Esta atualização estará disponível para o público geral (GA) até 1º de março de 2022.

Você pode enviar alterações ao seu aplicativo (como novos recursos ou até mesmo metadados) no Partner Center. Essas alterações exigem um novo processo de revisão.

Verifique o seguinte ao publicar atualizações:

* Não altere a ID do aplicativo.
* Incremente o número de versão do aplicativo.
* In Partner Center, don't select **Add a new app** to do the update. Go to your app's page instead.

### <a name="app-updates-requiring-user-consent"></a>Atualizações de aplicativo que exigem consentimento do usuário

Quando um usuário instala seu aplicativo, ele deve conceder ao aplicativo permissão para acessar os serviços e as informações que o aplicativo requer para funcionar. Na maioria dos casos, os usuários devem fazer isso uma vez e a nova versão do seu aplicativo são instaladas automaticamente.
No entanto, se você fizer qualquer uma das seguintes alterações em seu aplicativo, os usuários existentes deverão aceitar outra solicitação de permissão para instalar a atualização:

* Adicionar ou remover um bot.
* Altere a ID do bot.
* Modifique a configuração de notificação unidirecional de um bot.
* Modifique o suporte de um bot para carregar e baixar arquivos.
* Adicionar ou remover uma extensão de mensagem.
* Adicionar uma guia pessoal.
* Adicionar um canal e guia do grupo.
* Adicionar um conector.
* Modify configurations related to your Microsoft Azure Active Directory (Azure AD) app registration. For more information, see [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="fix-issues-with-your-published-app"></a>Corrigir problemas com seu aplicativo publicado

A Microsoft executa testes diários de automação em aplicativos listados na loja do Teams. Se forem identificados problemas com seu aplicativo, entraremos em contato com um relatório detalhado sobre como reproduzir os problemas e as recomendações para resolvê-los. Se você não puder corrigir os problemas em uma linha do tempo declarada, a listagem de aplicativos poderá ser removida da loja.

## <a name="promote-your-app-on-another-site"></a>Promover seu aplicativo em outro site

Quando seu aplicativo é listado na loja do Teams, você pode criar um link que inicia o Teams e exibe uma caixa de diálogo para instalar seu aplicativo. Você pode incluir esse link, por exemplo, com um botão de download na página de marketing do seu produto.

Crie o link usando a seguinte URL acrescentada à ID do aplicativo: `https://teams.microsoft.com/l/app/<your-app-id>`.

## <a name="complete-microsoft-365-certification"></a>Certificação Microsoft 365 Completa

[Certificação Microsoft 365](/microsoft-365-app-certification/docs/certification) oferece garantias de que os dados e a privacidade são adequadamente protegidos quando um aplicativo do Office ou um suplemento de terceiros é instalado em seu ecossistema Microsoft 365. A certificação confirma que seu aplicativo é compatível com as tecnologias da Microsoft, está em conformidade com as práticas recomendadas do Cloud App Security e tem suporte da Microsoft.

## <a name="stop-app-distribution"></a>Parar distribuição de aplicativos

Você pode remover um aplicativo do [Marketplace comercial da Microsoft](/azure/marketplace/overview) para impedir sua descoberta e uso.

Para interromper a distribuição de um aplicativo após a publicação, siga as etapas:

1. Na página **Visão geral do produto**, selecione **Parar de vender**. Ele remove o aplicativo do Microsoft AppSource.
1. Para iniciar a de-listagem do aplicativo, no **Partner Center**, selecione a página **Visão geral** e, em seguida, selecione **Parar de vender**.

Depois de interromper a distribuição de um aplicativo, você ainda poderá vê-lo no Partner Center com um status **Não disponível**. Se você decidir listar o aplicativo novamente, siga as instruções para [Publicar seu aplicativo na loja do Microsoft Teams](../publish.md).

## <a name="see-also"></a>Confira também

[Monetize seu aplicativo por meio do Marketplace Comercial da Microsoft](/office/dev/store/monetize-addins-through-microsoft-commercial-marketplace)
