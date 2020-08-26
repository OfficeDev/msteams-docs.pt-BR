---
title: Recursos da visualização do desenvolvedor público
description: Detalhes dos recursos do Microsoft Teams Public Developer Preview
keywords: recursos do desenvolvedor de visualização do teams
ms.openlocfilehash: 773e0334bddf45b7b86d31329b99607f3b70c534
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874839"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Recursos do Public Developer Preview for Microsoft Teams

A visualização do desenvolvedor inclui os seguintes novos recursos:

## <a name="tabs-single-sign-on-sso"></a>Logon único de guias (SSO)

Agora você pode usar o [logon único (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e móvel usando o SDK do teams JavaScript em uma página de conteúdo da Web. Um dos benefícios é que um usuário nunca precisa entrar; e depois de terem sido consentidas no aplicativo usando seu perfil: eles serão conectados automaticamente à sua guia (incluindo o móvel).

Nossa visualização do desenvolvedor está disponível nas versões 1,5 e posteriores do manifesto. Nossa implementação atual só pode obter uma quantidade limitada de APIs de gráfico, mas fornecemos uma solução alternativa para obter APIs de gráfico adicionais usando nossa API de autenticação existente.

## <a name="calls-and-online-meeting-bots"></a>Chamadas e bots de reunião online

Com a adição das [APIs do Microsoft Graph para chamadas e reuniões online](/graph/api/resources/communications-api-overview?view=graph-rest-beta), os aplicativos do Microsoft Teams agora podem interagir com usuários de maneiras ricas usando voz e vídeo. Essas APIs permitem que você adicione novos recursos do aplicativo, como resposta de voz interativa (IVR), controle de chamadas e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo área de trabalho e compartilhamento de aplicativos.

Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando pela [visão geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).

## <a name="image-enlarge-support"></a>Suporte ampliação de imagem

Agora, é possível que os bots indiquem quais imagens compartilhadas em cartões adaptáveis no Microsoft Teams podem ser ampliadas. Isso é útil para cenários como compartilhar guias visuais passo a passo detalhadas por meio de bots, que podem ser difíceis de ler para os usuários. Para tornar uma imagem expansível, basta sinalizá-la `allowExpand: true` conforme mostrado abaixo.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Isso fará com que o cliente da Web do teams/desktop processe um elemento ao passar o mouse sobre a imagem para permitir que o usuário expanda a imagem.

