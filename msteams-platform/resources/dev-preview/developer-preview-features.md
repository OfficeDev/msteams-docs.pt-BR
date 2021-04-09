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
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="7716b-104">Recursos na Visualização de Desenvolvedor Público do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7716b-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

<span data-ttu-id="7716b-105">A visualização do desenvolvedor inclui os seguintes novos recursos:</span><span class="sxs-lookup"><span data-stu-id="7716b-105">The developer preview includes the following new features:</span></span>

## <a name="app-customization"></a><span data-ttu-id="7716b-106">Personalização de aplicativos</span><span class="sxs-lookup"><span data-stu-id="7716b-106">App customization</span></span>

<span data-ttu-id="7716b-107">Agora você pode definir um conjunto selecionado de propriedades, que um administrador do Teams pode personalizar ou remarcar com base na necessidade de sua organização.</span><span class="sxs-lookup"><span data-stu-id="7716b-107">You can now define a select set of properties, which a Teams admin can customize or rebrand based on their organization's need.</span></span> <span data-ttu-id="7716b-108">Para obter mais informações, consulte [o recurso de personalização do aplicativo.](~/concepts/design/design-teams-app-overview.md)</span><span class="sxs-lookup"><span data-stu-id="7716b-108">For more information, see [app customization feature](~/concepts/design/design-teams-app-overview.md).</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="7716b-109">Sign-on único de guias (SSO)</span><span class="sxs-lookup"><span data-stu-id="7716b-109">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="7716b-110">Agora você pode usar o logon único [(SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) para fazer logon e autenticar um usuário na área de trabalho e no celular usando o SDK JavaScript do Teams em uma página de conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="7716b-110">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="7716b-111">Um dos benefícios é que um usuário nunca precisa entrar; e depois que eles consentiram com o aplicativo usando seu perfil: eles serão automaticamente insinuados na guia (incluindo celular).</span><span class="sxs-lookup"><span data-stu-id="7716b-111">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="7716b-112">Nossa visualização de desenvolvedor está disponível nas versões de manifesto 1.5 e superior.</span><span class="sxs-lookup"><span data-stu-id="7716b-112">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="7716b-113">Nossa implementação atual só pode obter uma quantidade limitada de APIs do Graph, no entanto, fornecemos uma solução alternativa para obter APIs adicionais do Graph usando nossa API de autenticação existente.</span><span class="sxs-lookup"><span data-stu-id="7716b-113">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="7716b-114">Chamadas e bots de reunião online</span><span class="sxs-lookup"><span data-stu-id="7716b-114">Calls and online meeting bots</span></span>

<span data-ttu-id="7716b-115">Com a adição de APIs do Microsoft Graph para chamadas e reuniões [online,](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)os aplicativos do Microsoft Teams agora podem interagir com os usuários de maneiras ricas usando voz e vídeo.</span><span class="sxs-lookup"><span data-stu-id="7716b-115">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="7716b-116">Essas APIs permitem adicionar novos recursos de aplicativo, como ivr (resposta de voz interativa), controle de chamada e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo o compartilhamento de área de trabalho e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7716b-116">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="7716b-117">Adicionamos uma nova seção sobre como criar e desenvolver chamadas e bots de reuniões online, começando com a visão [geral](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7716b-117">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>


## <a name="image-enlarge-support"></a><span data-ttu-id="7716b-118">Suporte para ampliação de imagem</span><span class="sxs-lookup"><span data-stu-id="7716b-118">Image enlarge support</span></span>

<span data-ttu-id="7716b-119">Agora é possível que os bots indiquem quais imagens compartilhadas em Cartões Adaptáveis no Teams têm permissão para serem ampliadas.</span><span class="sxs-lookup"><span data-stu-id="7716b-119">It is now possible for bots to indicate which images shared in Adaptive Cards in Teams are allowed to be enlarged.</span></span> <span data-ttu-id="7716b-120">Isso é útil para cenários como o compartilhamento detalhado de guias visuais passo a passo por meio de bots, o que pode ser difícil de ler para os usuários caso contrário.</span><span class="sxs-lookup"><span data-stu-id="7716b-120">This is useful for scenarios like sharing detailed step-by-step visual guides via bots which might be hard to read for users otherwise.</span></span> <span data-ttu-id="7716b-121">Para tornar uma imagem expansível, basta sinalizar `allowExpand: true` como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="7716b-121">To make an image expandable, just flag it `allowExpand: true` as shown below.</span></span>

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
<span data-ttu-id="7716b-122">Isso fará com que o cliente web/desktop do Teams renderiza um elemento ao passar o mouse sobre a imagem para permitir que o usuário expanda a imagem.</span><span class="sxs-lookup"><span data-stu-id="7716b-122">This will cause Teams web/desktop client to render an element on hover over the image to allow the user to expand the image.</span></span>

