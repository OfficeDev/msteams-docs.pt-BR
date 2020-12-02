---
title: Reordenar guias de aplicativos pessoais
description: Como reordenar as guias estáticas do aplicativo pessoal no seu aplicativo pessoal
keywords: desenvolvimento de guias do teams
ms.openlocfilehash: a8a7c3d23bac98ef1085a8f3443ca0fc92ae0a31
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49554823"
---
# <a name="reorder-personal-app-tabs"></a><span data-ttu-id="fe7ea-104">Reordenar guias de aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="fe7ea-104">Reorder personal app tabs</span></span>

<span data-ttu-id="fe7ea-105">Começando com o manifesto versão 1,7 os desenvolvedores podem reorganizar todas as guias em seus aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-105">Starting with manifest version 1.7 developers can rearrange all tabs in their personal app.</span></span> <span data-ttu-id="fe7ea-106">Em particular, um desenvolvedor pode mover a guia "chat de bot" (que sempre tem o padrão para a primeira posição) em qualquer lugar no cabeçalho da guia do aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-106">In particular, a developer can move the “bot chat” tab (which has always defaulted to the first position) anywhere in the personal app tab header.</span></span> <span data-ttu-id="fe7ea-107">Declaramos duas palavras-chave de EntityId da guia reservadas: "conversas" e "sobre".</span><span class="sxs-lookup"><span data-stu-id="fe7ea-107">We’ve declared two reserved tab entityId keywords: “conversations” and “about”.</span></span>

## <a name="moving-the-chatconversation-tab"></a><span data-ttu-id="fe7ea-108">Movendo a guia "chat/conversa"</span><span class="sxs-lookup"><span data-stu-id="fe7ea-108">Moving the “Chat/Conversation” tab</span></span>

<span data-ttu-id="fe7ea-109">Se você criar um bot com um escopo "pessoal", ele sempre será exibido na primeira posição de tabulação em um aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-109">If you create a bot with a “personal” scope, it will always show up in the first tab position in a personal app.</span></span> <span data-ttu-id="fe7ea-110">Se quiser movê-lo para outra posição, você precisará adicionar um objeto Tab estático ao manifesto com a palavra-chave reservada "conversas".</span><span class="sxs-lookup"><span data-stu-id="fe7ea-110">If you wish to move it to another position, you need to add a static tab object to your manifest with the reserved keyword “conversations”.</span></span> <span data-ttu-id="fe7ea-111">Sempre que você adicionar a guia "conversas" na matriz "staticTabs", será onde a guia conversa aparecerá na Web e na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-111">Wherever you add the “conversations” tab in the “staticTabs” array, that’s where the conversation tab will appear on web and desktop.</span></span> 

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

> [!NOTE]
> <span data-ttu-id="fe7ea-112">Observe que esse comportamento não é refletido no Mobile, pois o chat do Personal bot já tem um local exclusivo no aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-112">Note that this behavior is not reflected on mobile since the personal bot chat already has a dedicated place within the personal app.</span></span>

## <a name="moving-the-about-tab"></a><span data-ttu-id="fe7ea-113">Mover a guia "sobre"</span><span class="sxs-lookup"><span data-stu-id="fe7ea-113">Moving the “About” tab</span></span>

<span data-ttu-id="fe7ea-114">A guia "sobre" sempre é padrão para o final da barra de cabeçalho da guia aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-114">The “About” tab always defaults to the end of the personal app tab header bar.</span></span> <span data-ttu-id="fe7ea-115">Se quiser movê-lo para outra posição, você precisará usar o EntityId "sobre".</span><span class="sxs-lookup"><span data-stu-id="fe7ea-115">If you wish to move it to another position, you need to use the “about” entityId.</span></span>

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"about",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```
> [!NOTE]
> <span data-ttu-id="fe7ea-116">Observe que a guia sobre não é mostrada em celular.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-116">Note that the about tab is not shown on mobile.</span></span>

## <a name="example-code"></a><span data-ttu-id="fe7ea-117">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="fe7ea-117">Example code</span></span>

```json
{
   "staticTabs":[
      {
         "entityId":"homeTab",
         "name":"Home",
         "contentUrl":"https://www.contoso.com",
         "websiteUrl":" https://www.contoso.com ",
         "scopes":[
            "personal"
         ]
      },
      {
         "entityId":"about",
         "scopes":[
            "personal"
         ]
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```
