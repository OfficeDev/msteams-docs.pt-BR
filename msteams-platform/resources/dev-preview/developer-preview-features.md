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
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="c8a67-104">Recursos do Public Developer Preview for Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c8a67-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

<span data-ttu-id="c8a67-105">A visualização do desenvolvedor inclui os seguintes novos recursos:</span><span class="sxs-lookup"><span data-stu-id="c8a67-105">The developer preview includes the following new features:</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="c8a67-106">Logon único de guias (SSO)</span><span class="sxs-lookup"><span data-stu-id="c8a67-106">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="c8a67-107">Agora você pode usar o [logon único (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e móvel usando o SDK do teams JavaScript em uma página de conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="c8a67-107">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="c8a67-108">Um dos benefícios é que um usuário nunca precisa entrar; e depois de terem sido consentidas no aplicativo usando seu perfil: eles serão conectados automaticamente à sua guia (incluindo o móvel).</span><span class="sxs-lookup"><span data-stu-id="c8a67-108">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="c8a67-109">Nossa visualização do desenvolvedor está disponível nas versões 1,5 e posteriores do manifesto.</span><span class="sxs-lookup"><span data-stu-id="c8a67-109">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="c8a67-110">Nossa implementação atual só pode obter uma quantidade limitada de APIs de gráfico, mas fornecemos uma solução alternativa para obter APIs de gráfico adicionais usando nossa API de autenticação existente.</span><span class="sxs-lookup"><span data-stu-id="c8a67-110">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="c8a67-111">Chamadas e bots de reunião online</span><span class="sxs-lookup"><span data-stu-id="c8a67-111">Calls and online meeting bots</span></span>

<span data-ttu-id="c8a67-112">Com a adição das [APIs do Microsoft Graph para chamadas e reuniões online](/graph/api/resources/communications-api-overview?view=graph-rest-beta), os aplicativos do Microsoft Teams agora podem interagir com usuários de maneiras ricas usando voz e vídeo.</span><span class="sxs-lookup"><span data-stu-id="c8a67-112">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="c8a67-113">Essas APIs permitem que você adicione novos recursos do aplicativo, como resposta de voz interativa (IVR), controle de chamadas e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo área de trabalho e compartilhamento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c8a67-113">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="c8a67-114">Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando pela [visão geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c8a67-114">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>

## <a name="image-enlarge-support"></a><span data-ttu-id="c8a67-115">Suporte ampliação de imagem</span><span class="sxs-lookup"><span data-stu-id="c8a67-115">Image enlarge support</span></span>

<span data-ttu-id="c8a67-116">Agora, é possível que os bots indiquem quais imagens compartilhadas em cartões adaptáveis no Microsoft Teams podem ser ampliadas.</span><span class="sxs-lookup"><span data-stu-id="c8a67-116">It is now possible for bots to indicate which images shared in Adaptive Cards in Teams are allowed to be enlarged.</span></span> <span data-ttu-id="c8a67-117">Isso é útil para cenários como compartilhar guias visuais passo a passo detalhadas por meio de bots, que podem ser difíceis de ler para os usuários.</span><span class="sxs-lookup"><span data-stu-id="c8a67-117">This is useful for scenarios like sharing detailed step-by-step visual guides via bots which might be hard to read for users otherwise.</span></span> <span data-ttu-id="c8a67-118">Para tornar uma imagem expansível, basta sinalizá-la `allowExpand: true` conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="c8a67-118">To make an image expandable, just flag it `allowExpand: true` as shown below.</span></span>

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
<span data-ttu-id="c8a67-119">Isso fará com que o cliente da Web do teams/desktop processe um elemento ao passar o mouse sobre a imagem para permitir que o usuário expanda a imagem.</span><span class="sxs-lookup"><span data-stu-id="c8a67-119">This will cause Teams web/desktop client to render an element on hover over the image to allow the user to expand the image.</span></span>

