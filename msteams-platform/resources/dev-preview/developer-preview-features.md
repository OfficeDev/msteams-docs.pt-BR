---
title: Recursos na Visualização do Desenvolvedor Público
description: Detalhes dos recursos na Visualização de Desenvolvedor Público do Microsoft Teams
ms.topic: reference
keywords: Recursos de desenvolvedor de visualização do teams
ms.openlocfilehash: 05954383931444cd0fb53dc37d9f790257f7dd39
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634513"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Recursos na Visualização de Desenvolvedor Público do Microsoft Teams

A visualização do desenvolvedor inclui os seguintes novos recursos:

## <a name="app-customization"></a>Personalização de aplicativos

Agora você pode definir um conjunto selecionado de propriedades, que um administrador do Teams pode personalizar ou remarcar com base na necessidade de sua organização. Para obter mais informações, consulte [o recurso de personalização do aplicativo.](~/concepts/design/design-teams-app-overview.md)

## <a name="tabs-single-sign-on-sso"></a>Sign-on único de guias (SSO)

Agora você pode usar o logon único [(SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e no celular usando o SDK JavaScript do Teams em uma página de conteúdo da Web. Um dos benefícios é que um usuário nunca precisa entrar; e depois que eles consentiram com o aplicativo usando seu perfil: eles serão automaticamente insinuados na guia (incluindo celular).

Nossa visualização de desenvolvedor está disponível nas versões de manifesto 1.5 e superior. Nossa implementação atual só pode obter uma quantidade limitada de APIs do Graph, no entanto, fornecemos uma solução alternativa para obter APIs adicionais do Graph usando nossa API de autenticação existente.

## <a name="calls-and-online-meeting-bots"></a>Chamadas e bots de reunião online

Com a adição de APIs do Microsoft Graph para chamadas e reuniões [online,](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)os aplicativos do Microsoft Teams agora podem interagir com os usuários de maneiras ricas usando voz e vídeo. Essas APIs permitem adicionar novos recursos de aplicativo, como ivr (resposta de voz interativa), controle de chamada e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo o compartilhamento de área de trabalho e aplicativos.

Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando com a visão [geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).


## <a name="image-enlarge-support"></a>Suporte para ampliação de imagem

Agora é possível que os bots indiquem quais imagens compartilhadas em Cartões Adaptáveis no Teams têm permissão para serem ampliadas. Isso é útil para cenários como o compartilhamento detalhado de guias visuais passo a passo por meio de bots, o que pode ser difícil de ler para os usuários caso contrário. Para tornar uma imagem expansível, basta sinalizar `allowExpand: true` como mostrado abaixo.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Isso fará com que o cliente web/desktop do Teams renderiza um elemento ao passar o mouse sobre a imagem para permitir que o usuário expanda a imagem.

