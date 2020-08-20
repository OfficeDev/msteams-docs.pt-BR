---
title: Recursos da visualização do desenvolvedor público
description: Descreve os recursos da visualização pública de desenvolvedor do Microsoft Teams
keywords: recursos do desenvolvedor de visualização do teams
ms.openlocfilehash: e607a6c65253a5fd94f8a805f1264a567bb8fd24
ms.sourcegitcommit: 9fd61042e8be513c2b2bd8a33ab5e9e6498d65c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46819172"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Recursos do Public Developer Preview for Microsoft Teams

A visualização do desenvolvedor inclui os seguintes novos recursos:

## <a name="adaptive-cards-v12-support"></a>Suporte para cartões adaptáveis v 1.2

O suporte para [cartões adaptáveis v 1.2](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0) no Teams está agora disponível para o público em geral. No entanto, os [elementos de mídia](https://adaptivecards.io/explorer/Media.html) atualmente não têm suporte em cartões adaptáveis v 1.2 na plataforma do teams.

## <a name="tabs-single-sign-on-sso"></a>Logon único de guias (SSO)

Agora você pode usar o [logon único (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e móvel usando o SDK do teams JavaScript em uma página de conteúdo da Web. Um dos benefícios é que um usuário nunca precisa entrar; e depois de terem sido consentidas no aplicativo usando seu perfil: eles serão conectados automaticamente à sua guia (incluindo o móvel).

Nossa visualização do desenvolvedor está disponível nas versões 1,5 e posteriores do manifesto. Nossa implementação atual só pode obter uma quantidade limitada de APIs de gráfico, mas fornecemos uma solução alternativa para obter APIs de gráfico adicionais usando nossa API de autenticação existente.

## <a name="calls-and-online-meeting-bots"></a>Chamadas e bots de reunião online

Com a adição das [APIs do Microsoft Graph para chamadas e reuniões online](/graph/api/resources/communications-api-overview?view=graph-rest-beta), os aplicativos do Microsoft Teams agora podem interagir com usuários de maneiras ricas usando voz e vídeo. Essas APIs permitem que você adicione novos recursos do aplicativo, como resposta de voz interativa (IVR), controle de chamadas e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo área de trabalho e compartilhamento de aplicativos.

Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando pela [visão geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).
