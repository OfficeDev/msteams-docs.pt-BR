---
title: Mantendo e dando suporte ao seu aplicativo publicado
description: O que fazer depois de publicar seu aplicativo
ms.topic: how-to
keywords: teams post publish update certification app update manifest
ms.openlocfilehash: ce63b840307f7e12a5cd05a1c67aed017cf6199b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014324"
---
# <a name="maintain-and-support-your-published-app"></a>Manter e dar suporte ao seu aplicativo publicado 

Depois que seu aplicativo for aprovado e listado no catálogo de aplicativos público, você poderá aumentar seu alcance concluindo o Programa de Conformidade de Aplicativos do Microsoft 365 ou adicionando um botão de download ao seu site.

## <a name="microsoft-365-certified"></a>Microsoft 365 Certified

O Programa de Conformidade de Aplicativos do [Microsoft 365](./application-certification.md)é uma abordagem de três camadas para segurança e conformidade de aplicativos. Cada camada se baseia na próxima – oferecendo um programa em camadas para atender às necessidades do cliente. Você pode saber mais sobre a postura de segurança e conformidade dos aplicativos do Teams visitando a página [de conformidade.](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps)

## <a name="add-a-download-button-to-your-product-site"></a>Adicionar um botão de download ao site do produto

Se seu aplicativo estiver na loja global do Microsoft Teams, você poderá gerar um link para seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para que os usuários adicionem o aplicativo.
O formato é:  `https://teams.microsoft.com/l/app/<appId>` onde appID é o GUID declarado no manifesto enviado.
Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar o Trello.

## <a name="updating-your-existing-teams-app"></a>Atualizando seu aplicativo existente do Teams

* Não use o *botão Adicionar um novo aplicativo* para resubmitir seu aplicativo. Use o lado do aplicativo na guia Visão geral.
* A appId no manifesto atualizado deve ser a mesma do manifesto atual, com um número de versão incrementado.
* Incremente seu número de versão no manifesto se você fizer alterações no envio, incluindo o nome do aplicativo ou quaisquer metadados no manifesto.
* Envios atualizados são necessários para passar por um novo processo de revisão e validação.

## <a name="app-updates-and-the-user-consent-flow"></a>Atualizações de aplicativos e o fluxo de consentimento do usuário

Quando um usuário instala seu aplicativo, uma das primeiras coisas que ele faz é consentir em dar ao aplicativo permissão para acessar os serviços e informações que o aplicativo precisa para fazer seu trabalho. Na maioria dos casos, depois que você concluir uma atualização de aplicativo, a nova versão aparecerá automaticamente para os usuários finais. No entanto, há algumas atualizações no manifesto do [aplicativo teams](../../../../resources/schema/manifest-schema.md) que exigem a aceitação do usuário para ser concluída e podem disparar esse comportamento de consentimento outra vez:

 >[!div class="checklist"]
>
> * Um bot foi adicionado ou removido.
> * O valor exclusivo de um bot `botId` existente foi alterado.
> * O valor booliana de um bot `isNotificationOnly` existente foi alterado.
> * O valor booliana de um bot `supportsFiles` existente foi alterado.
> * Uma extensão de mensagens ( `composeExtensions` ) foi adicionada ou removida.
> * Um novo conector foi adicionado.
> * Uma nova guia estática/pessoal foi adicionada.
> * Uma nova guia de grupo/canal configurável foi adicionada.
> * Os `webApplicationInfo` valores foram alterados.
>

### <a name="images-of-user-consent-flow"></a>Imagens do fluxo de consentimento do usuário:

**Configurar um conector —** Essa tela será exibida somente para usuários do Teams.

![Configuração de fluxo de consentimento de um diagrama de conector](../../../../assets/images/connector-teams-consentflow.png)

**Fluxo de consentimento do** usuário - Essa tela é comum para escopo pessoal e de grupo. Aqui, marque a **caixa de seleção Consentimento em nome da** sua organização e escolha **Aceitar**.

![Diagrama de permissões](../../../../assets/images/user-consent-flow.png)
