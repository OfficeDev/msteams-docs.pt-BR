---
title: Publicar publicação
description: O que fazer após a publicação do aplicativo
keywords: publicar o Microsoft Teams postar certificado de atualização
ms.openlocfilehash: 05e4ea47bbf81967ccf086230bf0ad8c633f6e0b
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672547"
---
# <a name="maintain-and-support-your-published-app"></a>Manter e dar suporte ao aplicativo publicado 

Depois que o aplicativo é aprovado e listado no catálogo de aplicativos públicos, você pode aumentar seu alcance obtendo a certificação do aplicativo ou adicionando um botão de download ao seu site.

## <a name="application-certificate"></a>Certificado de aplicativo

A Microsoft fornece um [programa de certificação de aplicativo](./application-certification.md) que compila suas informações de aplicativo e as apresenta na página de [conformidade e segurança do aplicativo do Microsoft Teams](https://aka.ms/AppCertification). Essas informações destinam-se a ajudar os administradores a escolher aplicativos seguros para suas organizações.

## <a name="add-a-download-button-to-your-product-site"></a>Adicionar um botão de download ao seu site do produto

Se seu aplicativo estiver no Microsoft Teams Store, você poderá gerar um link para o seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para que os usuários adicionem o aplicativo.
O formato é: `https://teams.microsoft.com/l/app/<appId>` onde AppID é o GUID que eles declaram no manifesto enviado.
Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar o Trello.

## <a name="updating-your-existing-teams-app"></a>Atualizando seu aplicativo do teams existente

* Não use o botão *Adicionar um novo aplicativo* para reenviar seu aplicativo. Em vez disso, use o bloco para seu aplicativo na guia Visão geral.
* O appId no manifesto atualizado deve ser igual ao do manifesto atual, com um número de versão incrementado.
* Aumente o número da versão em seu manifesto.

### <a name="when-does-updating-your-app-trigger-the-user-consent-flow"></a>Quando a atualização do aplicativo dispara o fluxo de consentimento do usuário?

Quando um usuário instala o aplicativo uma das primeiras coisas que eles fazem é o consentimento para dar permissão ao aplicativo para acessar os serviços e informações de que o aplicativo precisa para realizar o trabalho. Ao atualizar seu aplicativo, isso pode disparar novamente esse comportamento de consentimento, especialmente se você tiver feito uma ou mais das seguintes alterações:

* Adição de um novo recurso a um aplicativo, como a adição de um bot a um aplicativo somente de tabulação.
* Alterar a matriz de permissões no manifesto.
* Aumente o número de versão do aplicativo em seu manifesto.
