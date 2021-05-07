---
title: Recursos na Visualização do Desenvolvedor Público
description: Detalhes dos recursos na visualização Microsoft Teams Desenvolvedor Público
ms.topic: reference
localization_priority: Normal
keywords: Recursos de desenvolvedor de visualização do teams
ms.openlocfilehash: 84683420a5c61bb1eb493f8191bfbcbe97f6fb46
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230901"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="46cd0-104">Recursos na Visualização de Desenvolvedor Público para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="46cd0-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="46cd0-105">Esta página será preterida em junho de 2021.</span><span class="sxs-lookup"><span data-stu-id="46cd0-105">This page will be deprecated in June 2021.</span></span> <span data-ttu-id="46cd0-106">Para obter informações sobre os recursos disponíveis para visualização do desenvolvedor, consulte [Novidades?](~/whats-new.md)</span><span class="sxs-lookup"><span data-stu-id="46cd0-106">For information on features available for developer preview, see [What's new?](~/whats-new.md)</span></span>

<span data-ttu-id="46cd0-107">A visualização do desenvolvedor inclui os seguintes novos recursos:</span><span class="sxs-lookup"><span data-stu-id="46cd0-107">The developer preview includes the following new features:</span></span>

## <a name="app-customization"></a><span data-ttu-id="46cd0-108">Personalização de aplicativos</span><span class="sxs-lookup"><span data-stu-id="46cd0-108">App customization</span></span>

<span data-ttu-id="46cd0-109">Agora você pode definir um conjunto selecionado de propriedades, que um administrador Teams pode personalizar ou remarcar com base na necessidade de sua organização.</span><span class="sxs-lookup"><span data-stu-id="46cd0-109">You can now define a select set of properties, which a Teams admin can customize or rebrand based on their organization's need.</span></span> <span data-ttu-id="46cd0-110">Para obter mais informações, consulte [o recurso de personalização do aplicativo.](~/concepts/design/design-teams-app-overview.md)</span><span class="sxs-lookup"><span data-stu-id="46cd0-110">For more information, see [app customization feature](~/concepts/design/design-teams-app-overview.md).</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="46cd0-111">Sign-on único de guias (SSO)</span><span class="sxs-lookup"><span data-stu-id="46cd0-111">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="46cd0-112">Agora você pode usar o logon único [(SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e no celular usando o SDK javascript Teams de uma página de conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="46cd0-112">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="46cd0-113">Um dos benefícios é que um usuário nunca precisa entrar; e depois que eles consentiram com o aplicativo usando seu perfil: eles serão automaticamente insinuados na guia (incluindo celular).</span><span class="sxs-lookup"><span data-stu-id="46cd0-113">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="46cd0-114">Nossa visualização de desenvolvedor está disponível nas versões de manifesto 1.5 e superior.</span><span class="sxs-lookup"><span data-stu-id="46cd0-114">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="46cd0-115">Nossa implementação atual só pode obter uma quantidade limitada de APIs Graph, no entanto, fornecemos uma solução alternativa para obter APIs adicionais Graph usando nossa API de autenticação existente.</span><span class="sxs-lookup"><span data-stu-id="46cd0-115">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="46cd0-116">Chamadas e bots de reunião online</span><span class="sxs-lookup"><span data-stu-id="46cd0-116">Calls and online meeting bots</span></span>

<span data-ttu-id="46cd0-117">Com a adição de APIs do Microsoft Graph para chamadas e reuniões [online,](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)Microsoft Teams aplicativos agora podem interagir com os usuários de maneiras ricas usando voz e vídeo.</span><span class="sxs-lookup"><span data-stu-id="46cd0-117">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="46cd0-118">Essas APIs permitem adicionar novos recursos de aplicativo, como ivr (resposta de voz interativa), controle de chamada e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo o compartilhamento de área de trabalho e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="46cd0-118">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="46cd0-119">Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando com a visão [geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46cd0-119">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>


## <a name="image-enlarge-support"></a><span data-ttu-id="46cd0-120">Suporte para ampliação de imagem</span><span class="sxs-lookup"><span data-stu-id="46cd0-120">Image enlarge support</span></span>

<span data-ttu-id="46cd0-121">Agora é possível que os bots indiquem quais imagens compartilhadas em Cartões Adaptáveis no Teams podem ser ampliadas.</span><span class="sxs-lookup"><span data-stu-id="46cd0-121">It is now possible for bots to indicate which images shared in Adaptive Cards in Teams are allowed to be enlarged.</span></span> <span data-ttu-id="46cd0-122">Isso é útil para cenários como o compartilhamento detalhado de guias visuais passo a passo por meio de bots, o que pode ser difícil de ler para os usuários caso contrário.</span><span class="sxs-lookup"><span data-stu-id="46cd0-122">This is useful for scenarios like sharing detailed step-by-step visual guides via bots which might be hard to read for users otherwise.</span></span> <span data-ttu-id="46cd0-123">Para tornar uma imagem expansível, basta sinalizar `allowExpand: true` como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="46cd0-123">To make an image expandable, just flag it `allowExpand: true` as shown below.</span></span>

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
<span data-ttu-id="46cd0-124">Isso fará com que Teams cliente web/desktop renderizar um elemento ao passar o mouse sobre a imagem para permitir que o usuário expanda a imagem.</span><span class="sxs-lookup"><span data-stu-id="46cd0-124">This will cause Teams web/desktop client to render an element on hover over the image to allow the user to expand the image.</span></span>
