---
title: Configurar o consentimento do administrador
description: Descreve como configurar o consentimento do administrador
ms.topic: how-to
ms.localizationpriority: medium
keywords: guias de autenticação do Microsoft Azure Active Directory (Azure AD) API do Graph
ms.openlocfilehash: dd954ef1ede05b6025b12512dfcee03044223642
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887931"
---
# <a name="configure-admin-consent"></a>Configurar o consentimento do administrador

Você pode definir o escopo do aplicativo para uma API exposta e determinar se os usuários podem consentir com esse escopo em diretórios em que o consentimento do usuário está habilitado. Você pode permitir que apenas administradores forneçam consentimento para permissões com privilégios mais altos.

## <a name="to-expose-an-api"></a>Para expor uma API

1. Selecione **Gerenciar** > **Expor uma API** no painel esquerdo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-api-menu.png" alt-text="Expor uma opção de menu de API." border="false":::

    A **página Expor uma API** é exibida.

1. Selecione **Definir para** gerar o URI da ID do aplicativo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-an-api.png" alt-text="Definir o URI da ID do aplicativo" border="false":::

    A seção para definir o URI da ID do aplicativo é exibida.

1. Insira o URI da ID do aplicativo e selecione **Salvar**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/set-app-id-uri.png" alt-text="URI da ID do Aplicativo" border="true":::

    Uma mensagem aparece no navegador informando que o URI da ID do aplicativo foi atualizado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-msg.png" alt-text="Mensagem de URI da ID do aplicativo" border="false":::

    O URI da ID do aplicativo é exibido na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-added.png" alt-text="URI da ID do aplicativo atualizado" border="false":::

## <a name="to-configure-api-scope"></a>Para configurar o escopo da API

1. Selecione **+ Adicionar um escopo** nos **Escopos definidos por esta seção de API** .

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-scope.png" alt-text="Selecionar escopo" border="true":::

    A **página Adicionar um escopo** é exibida.

1. Insira os detalhes do aplicativo para o escopo do aplicativo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-scope.png" alt-text="Adicionar detalhes do escopo" border="true":::

    1. Insira o nome do escopo. Este é um campo obrigatório.
    1. Selecione **Administradores e usuários** para configurar os usuários que podem dar consentimento para usar as credenciais de logon do usuário. A opção padrão é **somente Administradores**.
    1. Insira o nome **de exibição de consentimento do administrador**. Este é um campo obrigatório.
    1. Insira a descrição do consentimento do administrador. Este é um campo obrigatório.
    1. Insira o nome **de exibição de consentimento do usuário**.
    1. Insira a descrição da descrição de consentimento do usuário.
    1. Selecione a **opção Habilitado** para estado.
    1. Selecione **Adicionar escopo**.

    Uma mensagem aparece no navegador informando que o escopo foi adicionado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added-msg.png" alt-text="Mensagem de escopo adicionada" border="false":::

    O URI da ID do aplicativo é exibido na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added.png" alt-text="Escopo adicionado e exibido" border="false":::

## <a name="to-configure-authorized-client-application"></a>Para configurar o aplicativo cliente autorizado

1. Mova a página **Expor uma API para a** **seção aplicativo cliente** autorizado e selecione **+ Adicionar um aplicativo cliente**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/auth-client-apps.png" alt-text="Aplicativo cliente autorizado" border="true":::

    A **página Adicionar um aplicativo cliente** é exibida.

1. Insira os detalhes para adicionar um aplicativo cliente. Nesta seção, você adicionará dois aplicativos cliente.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-client-app.png" alt-text="Adicionar um aplicativo cliente" border="true":::

    1. Insira **1fec8e78-bce4-4aaf-ab1b-5451cc387264** como ID do cliente para aplicativos móveis ou de área de trabalho do Teams.
    1. Selecione a ID do aplicativo que você criou para seu aplicativo para os **escopos autorizados**.
    1. Selecione **Adicionar aplicativo**.

    Uma mensagem aparece no navegador informando que o aplicativo cliente foi adicionado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-app-auth-msg.png" alt-text="Mensagem adicionada pelo aplicativo cliente" border="false":::

    As IDs do aplicativo cliente são exibidas na página.

1. Repita a etapa anterior para adicionar o aplicativo cliente para o aplicativo Web do Teams.

    1. Insira **5e3ce6c0-2b1f-4285-8d4b-75ee78787346** como ID do cliente para o aplicativo Web.
    1. Selecione a ID do aplicativo que você criou para seu aplicativo para os **escopos autorizados**.
    1. Selecione **Adicionar aplicativo**.

    Uma mensagem aparece no navegador informando que o aplicativo cliente foi adicionado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-app-auth-msg.png" alt-text="Mensagem adicionada pelo aplicativo cliente para o aplicativo Web" border="false":::

    As IDs do aplicativo cliente são exibidas na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/client-app-added.png" alt-text="Aplicativo cliente adicionado e exibido" border="true":::
