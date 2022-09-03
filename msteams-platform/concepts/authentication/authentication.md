---
title: Autenticação de usuários de aplicativos
description: Saiba mais sobre os métodos de autenticação que você pode habilitar no aplicativo Teams, como SSO (logon único) e usando provedores OAuth de terceiros.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: b7ab4f007c0b7f9400e63d1654c5e0a930274468
ms.sourcegitcommit: 82c585d287d61924ce3a3bba3e9caeff35c9a27a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67587005"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Autenticar usuários no Microsoft Teams

A autenticação se trata de validar usuários de aplicativos e proteger os usuários do aplicativo e do aplicativo contra acesso injustificável. Você pode usar um método de autenticação adequado para seu aplicativo para validar os usuários do aplicativo que desejam usar o aplicativo do Teams.

Escolha adicionar autenticação para seu aplicativo de uma das duas maneiras:

- **Habilitar o SSO (** logon único) em um aplicativo do Teams: o SSO no Teams é um método de autenticação que usa a identidade do Teams de um usuário do aplicativo para fornecer acesso ao seu aplicativo. Um usuário que fez logon no Teams não precisa fazer logon novamente em seu aplicativo no ambiente do Teams. Com apenas um consentimento necessário do usuário do aplicativo, o aplicativo Teams recupera detalhes de acesso do Azure AD (Azure Active Directory). Depois que o usuário do aplicativo tiver dado consentimento, ele poderá acessar o aplicativo mesmo de outros dispositivos sem precisar ser validado novamente.

- **Habilitar** a autenticação usando o provedor OAuth de terceiros: você pode usar um provedor de identidade OAuth (IdP) de terceiros para autenticar os usuários do aplicativo. O usuário do aplicativo é registrado com o provedor de identidade, que tem uma relação de confiança com seu aplicativo. Quando o usuário tenta fazer logon, o provedor de identidade valida o usuário do aplicativo e fornece acesso ao seu aplicativo. Azure AD é um provedor OAuth de terceiros. Você pode usar outros provedores, como Google, Facebook, GitHub ou qualquer outro provedor.

## <a name="select-authentication-method"></a>Selecionar método de autenticação

Habilite a autenticação com IdPs OAuth de terceiros ou SSO em seu aplicativo de guia, aplicativo de bot e aplicativo de extensão de mensagens. Selecione um dos dois métodos para adicionar autenticação em seu aplicativo:

:::row:::
    :::column span="1":::
        SSO
    :::column-end:::
    :::column span="1":::
        &nbsp;
    :::column-end:::
    :::column span="1":::
        OAuth
    :::column-end:::
:::row-end:::
:::row:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/tab-sso-icon.png" alt-text="SSO para aplicativo guia" link="../../tabs/how-to/authentication/tab-sso-overview.md":::
    :::column-end:::
    :::column span="1":::
        <br>

        &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; **Aplicativo tab**  
        
    :::column-end:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/tab-app-idp.png" alt-text="Autenticação com provedor OAuth de terceiros para aplicativo guia." link="../../tabs/how-to/authentication/auth-tab-aad.md":::
    :::column-end:::
:::row-end:::
:::row:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/bot-sso-icon.png" alt-text="SSO para aplicativo de bot" link="../../bots/how-to/authentication/auth-aad-sso-bots.md":::
    :::column-end:::
    :::column span="1":::
        <br>

        &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; **Aplicativo de bot**
        
    :::column-end:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/bot-app-idp.png" alt-text="Autenticação com provedor OAuth de terceiros para aplicativo de bot." link="../../bots/how-to/authentication/add-authentication.md":::
    :::column-end:::
:::row-end:::
:::row:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/mex-sso-icon.png" alt-text="SSO para aplicativo de extensão de mensagens" link="../../messaging-extensions/how-to/enable-SSO-auth-me.md":::
    :::column-end:::
    :::column span="1":::
        <br>

        &nbsp;&nbsp; &nbsp; **Aplicativo de extensão de mensagem**
        
    :::column-end:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/mex-app-idp.png" alt-text="Autenticação com IdPs oAuth de terceiros para o aplicativo de extensão de mensagens." link="../../messaging-extensions/how-to/add-authentication.md":::
    :::column-end:::
:::row-end:::

> [!NOTE]
> A página autenticação silenciosa é movida para o módulo Recursos. Para obter mais informações, consulte [Autenticação silenciosa](../../tabs/how-to/authentication/auth-silent-aad.md).

## <a name="see-also"></a>Confira também

- [Habilitar o logon único em um aplicativo de guia](../../tabs/how-to/authentication/tab-sso-overview.md)
- [Fluxo de autenticação do Microsoft Teams para guias](~/tabs/how-to/authentication/auth-flow-tab.md)
- [Suporte de logon único para bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
- [Adicionar autenticação à sua extensão de mensagens](~/messaging-extensions/how-to/add-authentication.md)
