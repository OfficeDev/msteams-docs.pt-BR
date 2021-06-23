---
title: Aplicativos para Teams reuniões
author: surbhigupta
description: visão geral dos aplicativos Teams reuniões com base na função de usuário e participante
ms.topic: overview
ms.author: lajanuar
localization_priority: Normal
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: 0ba475e852b8dc673d33ac818077b3b0951ac5f9
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068572"
---
# <a name="apps-for-teams-meetings"></a><span data-ttu-id="f36a1-104">Aplicativos para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="f36a1-104">Apps for Teams meetings</span></span>

<span data-ttu-id="f36a1-105">As reuniões permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo.</span><span class="sxs-lookup"><span data-stu-id="f36a1-105">Meetings enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="f36a1-106">O aplicativo de reunião pode oferecer uma experiência do usuário para cada estágio do ciclo de vida da reunião, incluindo a experiência do aplicativo de pré-reunião, reunião e pós-reunião, dependendo do status do participante.</span><span class="sxs-lookup"><span data-stu-id="f36a1-106">The meeting app can deliver a user experience for each stage of the meeting lifecycle including pre-meeting, in-meeting, and post-meeting app experience, depending on the attendee's status.</span></span>

<span data-ttu-id="f36a1-107">Os usuários podem acessar aplicativos durante reuniões usando a galeria de guias, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f36a1-107">The users can access apps during meetings using the tab gallery, for example:</span></span>

* <span data-ttu-id="f36a1-108">Pré-estágio de um quadro Kanban.</span><span class="sxs-lookup"><span data-stu-id="f36a1-108">Pre-stage a Kanban board.</span></span>
* <span data-ttu-id="f36a1-109">Iniciar uma caixa de diálogo acionável na reunião.</span><span class="sxs-lookup"><span data-stu-id="f36a1-109">Launch an in-meeting actionable dialog.</span></span>
* <span data-ttu-id="f36a1-110">Crie uma pesquisa pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="f36a1-110">Create a post-meeting survey.</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/nKAy5rNDus4]

<span data-ttu-id="f36a1-111">Este artigo fornece uma visão geral da extensibilidade do aplicativo de reunião, referências de API, habilitar e configurar aplicativos para reuniões e cenas personalizadas do modo Juntos Teams.</span><span class="sxs-lookup"><span data-stu-id="f36a1-111">This article provides an overview of meeting app extensibility, API references, enable and configure apps for meetings, and custom Together Mode scenes in Teams.</span></span>

<span data-ttu-id="f36a1-112">Você pode aprimorar sua experiência de reunião usando o recurso de extensibilidade da reunião, que permite integrar seus aplicativos em reuniões.</span><span class="sxs-lookup"><span data-stu-id="f36a1-112">You can enhance your meeting experience by using the meeting extensibility feature, which enables you to integrate your apps within meetings.</span></span> <span data-ttu-id="f36a1-113">Ele também inclui diferentes estágios de um ciclo de vida de reunião, onde você pode integrar guias, bots e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f36a1-113">It also includes different stages of a meeting lifecycle, where you can integrate tabs, bots, and messaging extensions.</span></span> <span data-ttu-id="f36a1-114">Com as APIs de extensibilidade de reuniões, você pode identificar diferentes funções de participantes e tipos de usuário, obter eventos de reunião, gerar caixas de diálogo na reunião e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f36a1-114">With meetings extensibility APIs, you can identify different participant roles and user types, get meeting events, generate in-meeting dialogs, and so on.</span></span>

<span data-ttu-id="f36a1-115">Para personalizar Teams aplicativos para reuniões, você pode habilitar seus aplicativos para reuniões Teams atualizando o manifesto do aplicativo e também pode configurar seus aplicativos para cenários de reunião.</span><span class="sxs-lookup"><span data-stu-id="f36a1-115">To customize Teams with apps for meetings, you can enable your apps for Teams meetings by updating your app manifest and you can also configure your apps for meeting scenarios.</span></span>

<span data-ttu-id="f36a1-116">O novo recurso de cenas do Modo Juntos personalizado permite que os usuários colaborem em uma reunião com sua equipe em um só lugar sem serem separados por caixas.</span><span class="sxs-lookup"><span data-stu-id="f36a1-116">The new custom Together Mode scenes feature enables users to collaborate in a meeting with their team in one place without being separated by boxes.</span></span>

## <a name="see-also"></a><span data-ttu-id="f36a1-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="f36a1-117">See also</span></span>

* [<span data-ttu-id="f36a1-118">Tab</span><span class="sxs-lookup"><span data-stu-id="f36a1-118">Tab</span></span>](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [<span data-ttu-id="f36a1-119">Bot</span><span class="sxs-lookup"><span data-stu-id="f36a1-119">Bot</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="f36a1-120">Extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="f36a1-120">Messaging extension</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="f36a1-121">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f36a1-121">Design your app</span></span>](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="f36a1-122">Pré-requisitos e referências de API para aplicativos de reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="f36a1-122">Prerequisites and API references for apps in Teams meetings</span></span>](create-apps-for-teams-meetings.md)
* [<span data-ttu-id="f36a1-123">Cenas do modo Custom Together</span><span class="sxs-lookup"><span data-stu-id="f36a1-123">Custom Together Mode scenes</span></span>](~/apps-in-teams-meetings/teams-together-mode.md)

## <a name="next-step"></a><span data-ttu-id="f36a1-124">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="f36a1-124">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f36a1-125">Extensibilidade do aplicativo de reunião</span><span class="sxs-lookup"><span data-stu-id="f36a1-125">Meeting app extensibility</span></span>](meeting-app-extensibility.md)
