---
title: Criar segredo do cliente
description: Descreve a criação de segredo do cliente
ms.topic: how-to
ms.localizationpriority: medium
keywords: guias de autenticação do Microsoft Azure Active Directory (Azure AD) API do Graph
ms.openlocfilehash: 79116a0da845cd143de695424a904cf5b5968a15
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887930"
---
# <a name="create-client-secret"></a>Criar segredo do cliente

Um segredo do cliente é uma cadeia de caracteres que o aplicativo usa para provar sua identidade ao solicitar um token.

1. Selecione **Gerenciar** > **Certificados & segredos**.

2. Selecione **+ Novo segredo do cliente**.

    :::image type="content" source="../../../assets/images/adaptive-cards/client-secret.png" alt-text="Página de segredo do cliente":::

   A **página Adicionar um segredo do** cliente é exibida.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-client-secret.png" alt-text="Adicionar uma página de segredo do cliente" border="true":::

3. Insira a descrição.
4. Selecione a duração da validade do segredo.
5. Selecione **Adicionar**.

   Uma mensagem aparece no navegador informando que o segredo do cliente foi atualizado e o segredo do cliente é exibido na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/client-secret-added.png" alt-text="Segredo do cliente adicionado":::

6. Selecione o botão copiar ao lado do **valor do** segredo do cliente.
7. Salve o valor que você copiou para uso posterior.

   > [!NOTE]
   > Copie o valor do segredo do cliente logo após a criação. O valor é visível somente no momento em que o segredo do cliente é criado e não pode ser exibido depois disso.
