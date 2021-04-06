---
title: Mantendo e dando suporte ao aplicativo publicado
description: O que fazer depois de publicar seu aplicativo
ms.topic: how-to
keywords: teams post publish update certification app update update manifest
ms.openlocfilehash: 8644db5e329e15d77062553eda4a41a36b2740ee
ms.sourcegitcommit: e78c9f51c4538212c53bb6c6a45a09d994896f09
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2021
ms.locfileid: "51585831"
---
# <a name="maintain-and-support-your-published-app"></a>Manter e dar suporte ao seu aplicativo publicado 

Depois que seu aplicativo for aprovado e listado no catálogo de aplicativos públicos, você poderá aumentar seu alcance concluindo o Programa de Conformidade de Aplicativos do Microsoft 365 ou adicionando um botão de download em seu site.

## <a name="microsoft-365-certified"></a>Microsoft 365 Certified

O Programa de Conformidade de Aplicativos do [Microsoft 365](./application-certification.md)é uma abordagem de três camadas para segurança e conformidade do aplicativo. Cada camada se acumula na próxima – oferecendo um programa em camadas para atender às necessidades do cliente. Você pode saber mais sobre a postura de segurança e conformidade dos aplicativos do Teams visitando a página [de conformidade](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).

## <a name="add-a-download-button-to-your-product-site"></a>Adicionar um botão de download ao site do produto

Se seu aplicativo estiver na loja global do Microsoft Teams, você poderá gerar um link para seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para os usuários adicionarem o aplicativo.
O formato é:  `https://teams.microsoft.com/l/app/<appId>` onde appID é o GUID declarado no manifesto enviado.
Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar Trello.

## <a name="updating-your-existing-teams-app"></a>Atualizando seu aplicativo existente do Teams

* Não use o *botão Adicionar um novo aplicativo* para reabrir o aplicativo. Use o azulejo para seu aplicativo na guia Visão geral.
* O appId no manifesto atualizado deve ser o mesmo do manifesto atual, com um número de versão incrementado.
* Incremente seu número de versão no manifesto se você fizer alterações no envio, incluindo o nome do aplicativo ou quaisquer metadados no manifesto.
* Os envios atualizados são necessários para passar por um novo processo de revisão e validação.

## <a name="app-updates-and-the-user-consent-flow"></a>Atualizações de aplicativos e o fluxo de consentimento do usuário

Quando um usuário instala seu aplicativo, uma das primeiras coisas que ele faz é consentir em dar ao aplicativo permissão para acessar os serviços e informações que o aplicativo precisa para fazer seu trabalho. Na maioria dos casos, depois de concluir uma atualização de aplicativo, a nova versão aparecerá automaticamente para usuários finais. No entanto, há algumas atualizações no manifesto do [aplicativo do Teams](../../../../resources/schema/manifest-schema.md) que exigem que a aceitação do usuário seja concluída e podem reacionar esse comportamento de consentimento:

 >[!div class="checklist"]
>
> * Um bot é adicionado ou removido.
> * O valor exclusivo de um bot `botId` existente é alterado.
> * O valor boolano de um `isNotificationOnly` bot existente é alterado.
> * O valor booleano ou bot `supportsFiles` `supportsCalling` existente é alterado.
> * Uma extensão de mensagens `composeExtensions` é adicionada ou removida.
> * Um novo conector é adicionado.
> * Uma nova guia estática ou pessoal é adicionada.
> * Um novo grupo configurável ou uma guia de canal é adicionado.
> * As propriedades internas `webApplicationInfo` são alteradas. Para alterações em `webApplicationInfo` , o consentimento só é necessário no escopo do Teams.

### <a name="images-of-user-consent-flow"></a>Imagens do fluxo de consentimento do usuário:

**Configurar um conector** — essa tela aparecerá somente para usuários do Teams.

![Configuração de fluxo de consentimento um diagrama de conector](../../../../assets/images/connector-teams-consentflow.png)

**Fluxo de consentimento do usuário** - Essa tela é comum para escopo pessoal e de grupo. Aqui, selecione a **caixa de seleção Consentimento em nome** da sua organização e escolha **Aceitar**.

![Diagrama de permissões](../../../../assets/images/user-consent-flow.png)
