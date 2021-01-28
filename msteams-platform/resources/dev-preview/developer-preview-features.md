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
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="3f8ff-104">Recursos na Visualização do Desenvolvedor Público para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3f8ff-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

<span data-ttu-id="3f8ff-105">A visualização do desenvolvedor inclui os seguintes novos recursos:</span><span class="sxs-lookup"><span data-stu-id="3f8ff-105">The developer preview includes the following new features:</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="3f8ff-106">Tabs single sign-on (SSO)</span><span class="sxs-lookup"><span data-stu-id="3f8ff-106">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="3f8ff-107">Agora você pode usar o logon único [(SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e em dispositivos móveis usando o SDK JavaScript do Teams em uma página de conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-107">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="3f8ff-108">Um dos benefícios é que um usuário nunca precisa entrar; e depois que eles concordarem com o aplicativo usando seu perfil: eles entrarão automaticamente na guia (incluindo dispositivos móveis).</span><span class="sxs-lookup"><span data-stu-id="3f8ff-108">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="3f8ff-109">Nossa visualização de desenvolvedor está disponível nas versões de manifesto 1.5 e superior.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-109">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="3f8ff-110">Nossa implementação atual só pode obter uma quantidade limitada de APIs do Graph, no entanto, fornecemos uma solução alternativa para obter APIs adicionais do Graph usando nossa API de autenticação existente.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-110">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="3f8ff-111">Bots de chamadas e reuniões online</span><span class="sxs-lookup"><span data-stu-id="3f8ff-111">Calls and online meeting bots</span></span>

<span data-ttu-id="3f8ff-112">Com a adição de APIs do Microsoft Graph para chamadas e reuniões [online,](/graph/api/resources/communications-api-overview?view=graph-rest-beta)os aplicativos do Microsoft Teams agora podem interagir com os usuários de maneiras ricas usando voz e vídeo.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-112">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="3f8ff-113">Essas APIs permitem adicionar novos recursos do aplicativo, como IVR (resposta interativa de voz), controle de chamada e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo o compartilhamento de área de trabalho e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-113">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="3f8ff-114">Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando com a visão [geral.](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)</span><span class="sxs-lookup"><span data-stu-id="3f8ff-114">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>

## <a name="image-enlarge-support"></a><span data-ttu-id="3f8ff-115">Suporte para ampliação de imagem</span><span class="sxs-lookup"><span data-stu-id="3f8ff-115">Image enlarge support</span></span>

<span data-ttu-id="3f8ff-116">Agora é possível que os bots indiquem quais imagens compartilhadas em Cartões Adaptáveis no Teams têm permissão para serem ampliadas.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-116">It is now possible for bots to indicate which images shared in Adaptive Cards in Teams are allowed to be enlarged.</span></span> <span data-ttu-id="3f8ff-117">Isso é útil para cenários como o compartilhamento detalhado de guias visuais passo a passo por meio de bots que podem ser difíceis de ler para os usuários caso contrário.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-117">This is useful for scenarios like sharing detailed step-by-step visual guides via bots which might be hard to read for users otherwise.</span></span> <span data-ttu-id="3f8ff-118">Para tornar uma imagem expansível, basta sinalizar como `allowExpand: true` mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-118">To make an image expandable, just flag it `allowExpand: true` as shown below.</span></span>

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
<span data-ttu-id="3f8ff-119">Isso fará com que o cliente web/desktop do Teams renderizar um elemento ao passar o mouse sobre a imagem para permitir que o usuário expanda a imagem.</span><span class="sxs-lookup"><span data-stu-id="3f8ff-119">This will cause Teams web/desktop client to render an element on hover over the image to allow the user to expand the image.</span></span>

