---
title: Recursos da visualização do desenvolvedor público
description: Descreve os recursos da visualização pública de desenvolvedor do Microsoft Teams
keywords: recursos do desenvolvedor de visualização do teams
ms.openlocfilehash: abec097d9f3b6fb48a4a50cb26d73cf811151149
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672482"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Recursos do Public Developer Preview for Microsoft Teams

A visualização do desenvolvedor inclui os seguintes novos recursos:

## <a name="mention-support-in-adaptive-cards"></a>Mencione o suporte em cartões adaptáveis

Agora você pode adicionar @ menção dentro de um corpo de cartão adaptável para bots e respostas de extensão de mensagens. @ as menção nos cartões seguem a mesma lógica de notificação e renderização que as mencionadas com base em mensagem regular. Observe que as mencionadas por cartão só são compatíveis com clientes da Web e de desktop atuais, com suporte para renderização em clientes móveis em breve.

## <a name="adaptive-12-support"></a>Suporte 1,2 adaptável

O Microsoft Teams agora oferece suporte à [versão adaptável 1,2](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0) na visualização do desenvolvedor. Observe que os [elementos de mídia](https://adaptivecards.io/explorer/Media.html) ainda não têm suporte.

## <a name="tabs-single-sign-on"></a>Logon único de guias

Agora você pode usar o [logon único (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e móvel usando o SDK do teams JavaScript em uma página de conteúdo da Web. Um dos benefícios é que um usuário nunca precisa entrar; e depois de terem sido consentidas no aplicativo usando seu perfil: eles serão conectados automaticamente à sua guia (incluindo o móvel).

Nossa visualização do desenvolvedor está disponível nas versões 1,5 e posteriores do manifesto. Nossa implementação atual só pode obter uma quantidade limitada de APIs de gráfico, mas fornecemos uma solução alternativa para obter APIs de gráfico adicionais usando nossa API de autenticação existente.

## <a name="personal-apps-static-tabs-and-1-1-bots-enabled-on-mobile"></a>Aplicativos pessoais (guias estáticas e bots 1-1) habilitados no Mobile

Os aplicativos pessoais instalados (guias estáticos e bots 1-1) já estão disponíveis na bandeja de aplicativos em dispositivos móveis. Consulte [diretrizes de design para dispositivos móveis](~/tabs/design/tabs-mobile.md) para obter diretrizes de design. Os aplicativos podem ser instalados apenas de um cliente da Web ou da área de trabalho e podem levar até 4 horas para que estejam disponíveis no celular após a instalação.

Isso inclui a capacidade de um administrador do sistema de fixar um aplicativo por meio de [políticas de configuração de aplicativos](/microsoftteams/teams-app-setup-policies). Os aplicativos que foram afixados serão exibidos na gaveta de aplicativos.

## <a name="calls-and-online-meeting-bots"></a>Chamadas e bots de reunião online

Com a adição das [APIs do Microsoft Graph para chamadas e reuniões online](/graph/api/resources/communications-api-overview?view=graph-rest-beta), os aplicativos do Microsoft Teams agora podem interagir com usuários de maneiras ricas usando voz e vídeo. Essas APIs permitem que você adicione novos recursos do aplicativo, como resposta de voz interativa (IVR), controle de chamadas e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo área de trabalho e compartilhamento de aplicativos.

Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando pela [visão geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).