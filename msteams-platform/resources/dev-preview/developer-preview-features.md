---
title: Recursos na Visualização do Desenvolvedor Público
description: Detalhes dos recursos no Microsoft Teams Public Developer Preview
ms.topic: reference
keywords: recursos de desenvolvedor de visualização do Teams
ms.openlocfilehash: 3275ef7ac0d4ba052f417f6e852f48e2fdf267f5
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014352"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Recursos na Visualização do Desenvolvedor Público para o Microsoft Teams

A visualização do desenvolvedor inclui os seguintes novos recursos:

## <a name="tabs-single-sign-on-sso"></a>Tabs single sign-on (SSO)

Agora você pode usar o logon único [(SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e em dispositivos móveis usando o SDK JavaScript do Teams em uma página de conteúdo da Web. Um dos benefícios é que um usuário nunca precisa entrar; e depois que eles concordarem com o aplicativo usando seu perfil: eles entrarão automaticamente na guia (incluindo dispositivos móveis).

Nossa visualização de desenvolvedor está disponível nas versões de manifesto 1.5 e superior. Nossa implementação atual só pode obter uma quantidade limitada de APIs do Graph, no entanto, fornecemos uma solução alternativa para obter APIs adicionais do Graph usando nossa API de autenticação existente.

## <a name="calls-and-online-meeting-bots"></a>Bots de chamadas e reuniões online

Com a adição de APIs do Microsoft Graph para chamadas e reuniões [online,](/graph/api/resources/communications-api-overview?view=graph-rest-beta)os aplicativos do Microsoft Teams agora podem interagir com os usuários de maneiras ricas usando voz e vídeo. Essas APIs permitem adicionar novos recursos do aplicativo, como IVR (resposta interativa de voz), controle de chamada e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo o compartilhamento de área de trabalho e aplicativos.

Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando com a visão [geral.](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

## <a name="image-enlarge-support"></a>Suporte para ampliação de imagem

Agora é possível que os bots indiquem quais imagens compartilhadas em Cartões Adaptáveis no Teams têm permissão para serem ampliadas. Isso é útil para cenários como o compartilhamento detalhado de guias visuais passo a passo por meio de bots que podem ser difíceis de ler para os usuários caso contrário. Para tornar uma imagem expansível, basta sinalizar como `allowExpand: true` mostrado abaixo.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Isso fará com que o cliente web/desktop do Teams renderizar um elemento ao passar o mouse sobre a imagem para permitir que o usuário expanda a imagem.

