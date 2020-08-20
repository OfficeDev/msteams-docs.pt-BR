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
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="1cc29-104">Recursos do Public Developer Preview for Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1cc29-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

<span data-ttu-id="1cc29-105">A visualização do desenvolvedor inclui os seguintes novos recursos:</span><span class="sxs-lookup"><span data-stu-id="1cc29-105">The developer preview includes the following new features:</span></span>

## <a name="adaptive-cards-v12-support"></a><span data-ttu-id="1cc29-106">Suporte para cartões adaptáveis v 1.2</span><span class="sxs-lookup"><span data-stu-id="1cc29-106">Adaptive cards v1.2 support</span></span>

<span data-ttu-id="1cc29-107">O suporte para [cartões adaptáveis v 1.2](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0) no Teams está agora disponível para o público em geral.</span><span class="sxs-lookup"><span data-stu-id="1cc29-107">Support for [Adaptive cards v1.2](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0) in Teams is now available to the general public.</span></span> <span data-ttu-id="1cc29-108">No entanto, os [elementos de mídia](https://adaptivecards.io/explorer/Media.html) atualmente não têm suporte em cartões adaptáveis v 1.2 na plataforma do teams.</span><span class="sxs-lookup"><span data-stu-id="1cc29-108">However, [Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="1cc29-109">Logon único de guias (SSO)</span><span class="sxs-lookup"><span data-stu-id="1cc29-109">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="1cc29-110">Agora você pode usar o [logon único (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e móvel usando o SDK do teams JavaScript em uma página de conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="1cc29-110">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="1cc29-111">Um dos benefícios é que um usuário nunca precisa entrar; e depois de terem sido consentidas no aplicativo usando seu perfil: eles serão conectados automaticamente à sua guia (incluindo o móvel).</span><span class="sxs-lookup"><span data-stu-id="1cc29-111">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="1cc29-112">Nossa visualização do desenvolvedor está disponível nas versões 1,5 e posteriores do manifesto.</span><span class="sxs-lookup"><span data-stu-id="1cc29-112">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="1cc29-113">Nossa implementação atual só pode obter uma quantidade limitada de APIs de gráfico, mas fornecemos uma solução alternativa para obter APIs de gráfico adicionais usando nossa API de autenticação existente.</span><span class="sxs-lookup"><span data-stu-id="1cc29-113">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="1cc29-114">Chamadas e bots de reunião online</span><span class="sxs-lookup"><span data-stu-id="1cc29-114">Calls and online meeting bots</span></span>

<span data-ttu-id="1cc29-115">Com a adição das [APIs do Microsoft Graph para chamadas e reuniões online](/graph/api/resources/communications-api-overview?view=graph-rest-beta), os aplicativos do Microsoft Teams agora podem interagir com usuários de maneiras ricas usando voz e vídeo.</span><span class="sxs-lookup"><span data-stu-id="1cc29-115">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="1cc29-116">Essas APIs permitem que você adicione novos recursos do aplicativo, como resposta de voz interativa (IVR), controle de chamadas e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo área de trabalho e compartilhamento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1cc29-116">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="1cc29-117">Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando pela [visão geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc29-117">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>
