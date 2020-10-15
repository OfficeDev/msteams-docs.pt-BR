---
title: Publicar publicação
description: O que fazer após a publicação do aplicativo
keywords: publicar publicação atualizar manifesto de atualização de aplicativo de certificação
ms.openlocfilehash: 58e81688ab9a8b55d2b035fc9b43cb58dddb6133
ms.sourcegitcommit: 25afe104d10c9a6a2849decf5ec1d08969d827c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "48465912"
---
# <a name="maintain-and-support-your-published-app"></a>Manter e dar suporte ao seu aplicativo publicado 

Depois que o aplicativo é aprovado e listado no catálogo de aplicativos públicos, você pode aumentar seu alcance, concluindo o programa de conformidade do aplicativo Microsoft 365 ou adicionando um botão de download no seu site.

## <a name="microsoft-365-certified"></a>Certificado pela Microsoft 365

O [programa de conformidade do Microsoft 365 app](./application-certification.md), é uma abordagem de três camadas para a segurança do aplicativo e conformidade. Cada camada é baseada na próxima – oferecendo um programa em camadas para atender às necessidades do cliente. Você pode saber mais sobre a postura de segurança e conformidade de aplicativos do teams visitando a [página conformidade](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).

## <a name="add-a-download-button-to-your-product-site"></a>Adicionar um botão de download ao seu site do produto

Se seu aplicativo estiver no repositório global do Microsoft Teams, você poderá gerar um link para o seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para que os usuários adicionem o aplicativo.
O formato é:  `https://teams.microsoft.com/l/app/<appId>` onde AppID é o GUID que eles declaram no manifesto enviado.
Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar o Trello.

## <a name="updating-your-existing-teams-app"></a>Atualizando seu aplicativo do teams existente

* Não use o botão *Adicionar um novo aplicativo* para reenviar seu aplicativo. Em vez disso, use o bloco para seu aplicativo na guia Visão geral.
* O appId no manifesto atualizado deve ser igual ao do manifesto atual, com um número de versão incrementado.
* Aumente o número da versão no manifesto se você fizer qualquer alteração no envio, incluindo o nome do aplicativo ou qualquer metadado no manifesto.
* Envios atualizados são necessários para passar por um novo processo de revisão e validação.

## <a name="app-updates-and-the-user-consent-flow"></a>Atualizações de aplicativos e o fluxo de consentimento do usuário

Quando um usuário instala o aplicativo uma das primeiras coisas que eles fazem é o consentimento para dar permissão ao aplicativo para acessar os serviços e informações de que o aplicativo precisa para realizar o trabalho. Na maioria dos casos, após concluir uma atualização de aplicativo, a nova versão aparecerá automaticamente para os usuários finais. No entanto, há algumas atualizações para o [manifesto do aplicativo do teams](../../../../resources/schema/manifest-schema.md) que exigem a aceitação do usuário para serem concluídas e podem disparar novamente esse comportamento de consentimento:

 >[!div class="checklist"]
>
> * Um bot foi adicionado ou removido.
> * Um valor exclusivo de bot existente `botId` foi alterado.
> * Um `isNotificationOnly` valor booliano de bot existente foi alterado.
> * Um `supportsFiles` valor booliano de bot existente foi alterado.
> * Uma extensão de mensagens ( `composeExtensions` ) foi adicionada ou removida.
> * Um novo conector foi adicionado.
> * Uma nova guia estática/pessoal foi adicionada.
> * Uma nova guia de grupo/canal configurável foi adicionada.
> * Os `webApplicationInfo` valores foram alterados.
>
