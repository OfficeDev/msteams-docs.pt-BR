---
title: Recursos na Visualização do Desenvolvedor Público
description: Detalhes dos recursos na visualização Microsoft Teams Desenvolvedor Público
ms.topic: reference
localization_priority: Normal
keywords: Recursos de desenvolvedor de visualização do teams
ms.openlocfilehash: f24f95245707097cb5fc79c041582efb5e1f11ef29877855003baf3707842c4c
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57704393"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Recursos na Visualização de Desenvolvedor Público para Microsoft Teams

> [!NOTE]
> Esta página será preterida em junho de 2021. Para obter informações sobre os recursos disponíveis para visualização do desenvolvedor, consulte [Novidades?](~/whats-new.md)

A visualização do desenvolvedor inclui os seguintes novos recursos:

## <a name="app-customization"></a>Personalização de aplicativos

Agora você pode definir um conjunto selecionado de propriedades, que um administrador Teams pode personalizar ou remarcar com base na necessidade de sua organização. Para obter mais informações, consulte [o recurso de personalização do aplicativo.](~/concepts/design/design-teams-app-overview.md)

## <a name="tabs-single-sign-on-sso"></a>Sign-on único de guias (SSO)

Agora você pode usar o logon único [(SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e no celular usando o SDK javascript Teams de uma página de conteúdo da Web. Um dos benefícios é que um usuário nunca precisa entrar; e depois que eles consentiram com o aplicativo usando seu perfil: eles serão automaticamente insinuados na guia (incluindo celular).

Nossa visualização de desenvolvedor está disponível nas versões de manifesto 1.5 e superior. Nossa implementação atual só pode obter uma quantidade limitada de APIs Graph, no entanto, fornecemos uma solução alternativa para obter APIs adicionais Graph usando nossa API de autenticação existente.

## <a name="calls-and-online-meeting-bots"></a>Chamadas e bots de reunião online

Com a adição de APIs do Microsoft Graph para chamadas e reuniões [online,](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)Microsoft Teams aplicativos agora podem interagir com os usuários de maneiras ricas usando voz e vídeo. Essas APIs permitem adicionar novos recursos de aplicativo, como ivr (resposta de voz interativa), controle de chamada e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo o compartilhamento de área de trabalho e aplicativos.

Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando com a visão [geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).


## <a name="image-enlarge-support"></a>Suporte para ampliação de imagem

Agora é possível que os bots indiquem quais imagens compartilhadas em Cartões Adaptáveis no Teams podem ser ampliadas. Isso é útil para cenários como o compartilhamento detalhado de guias visuais passo a passo por meio de bots, o que pode ser difícil de ler para os usuários caso contrário. Para tornar uma imagem expansível, basta sinalizar `allowExpand: true` como mostrado abaixo.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Isso fará com que Teams cliente web/desktop renderizar um elemento ao passar o mouse sobre a imagem para permitir que o usuário expanda a imagem.
