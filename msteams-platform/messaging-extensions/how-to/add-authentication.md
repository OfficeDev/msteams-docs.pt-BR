---
title: Adicionar autenticação à sua extensão de mensagens
author: clearab
description: Como adicionar autenticação a uma extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f7ebbcd99b1ec35900de7ec2f54f93263918e945
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672516"
---
# <a name="add-authentication-to-your-messaging-extension"></a><span data-ttu-id="4e35e-103">Adicionar autenticação à sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4e35e-103">Add authentication to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a><span data-ttu-id="4e35e-104">Identificar o usuário</span><span class="sxs-lookup"><span data-stu-id="4e35e-104">Identify the user</span></span>

<span data-ttu-id="4e35e-105">Todas as solicitações para seus serviços incluem a ID ofuscada do usuário que realizou a solicitação, bem como o nome de exibição do usuário e a ID de objeto do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="4e35e-105">Every request to your services includes the obfuscated ID of the user that performed the request, as well as the user's display name and Azure Active Directory object ID.</span></span>

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

<span data-ttu-id="4e35e-106">Os `id` valores `aadObjectId` e são garantidos do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4e35e-106">The `id` and `aadObjectId` values are guaranteed to be that of the authenticated Teams user.</span></span> <span data-ttu-id="4e35e-107">Eles podem ser usados como chaves para procurar credenciais ou qualquer estado em cache em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="4e35e-107">They can be used as keys to look up credentials or any cached state in your service.</span></span> <span data-ttu-id="4e35e-108">Além disso, cada solicitação contém a ID de locatário do Azure Active Directory do usuário, que pode ser usada para identificar a organização do usuário.</span><span class="sxs-lookup"><span data-stu-id="4e35e-108">In addition, each request contains the Azure Active Directory tenant ID of the user, which can be used to identify the user’s organization.</span></span> <span data-ttu-id="4e35e-109">Se aplicável, a solicitação também contém as IDs de canal e equipe das quais a solicitação foi originada.</span><span class="sxs-lookup"><span data-stu-id="4e35e-109">If applicable, the request also contains the team and channel IDs from which the request originated.</span></span>

## <a name="authentication"></a><span data-ttu-id="4e35e-110">Autenticação</span><span class="sxs-lookup"><span data-stu-id="4e35e-110">Authentication</span></span>

<span data-ttu-id="4e35e-111">Se o serviço exigir autenticação do usuário, você precisará entrar no usuário antes de poder usar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4e35e-111">If your service requires user authentication, you need to sign in the user before he or she can use the messaging extension.</span></span> <span data-ttu-id="4e35e-112">Se você escreveu um bot ou uma guia que entra no usuário, esta seção deve ser familiar.</span><span class="sxs-lookup"><span data-stu-id="4e35e-112">If you have written a bot or a tab that signs in the user, this section should be familiar.</span></span>

<span data-ttu-id="4e35e-113">A sequência é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="4e35e-113">The sequence is as follows:</span></span>

1. <span data-ttu-id="4e35e-114">O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="4e35e-114">User issues a query, or the default query is automatically sent to your service.</span></span>
2. <span data-ttu-id="4e35e-115">Seu serviço verifica se o usuário foi autenticado pela primeira vez inspecionando a ID de usuário do teams.</span><span class="sxs-lookup"><span data-stu-id="4e35e-115">Your service checks whether the user has first authenticated by inspecting the Teams user ID.</span></span>
3. <span data-ttu-id="4e35e-116">Se o usuário não tiver sido autenticado, envie uma `auth` resposta com uma `openUrl` ação sugerida, incluindo a URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="4e35e-116">If the user has not authenticated, send back an `auth` response with an `openUrl` suggested action including the authentication URL.</span></span>
4. <span data-ttu-id="4e35e-117">O cliente do Microsoft Teams inicia uma janela pop-up hospedando sua página da Web usando a URL de autenticação determinada.</span><span class="sxs-lookup"><span data-stu-id="4e35e-117">The Microsoft Teams client launches a pop-up window hosting your webpage using the given authentication URL.</span></span>
5. <span data-ttu-id="4e35e-118">Após o usuário entrar, você deve fechar sua janela e enviar um "código de autenticação" para o cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="4e35e-118">After the user signs in, you should close your window and send an "authentication code" to the Teams client.</span></span>
6. <span data-ttu-id="4e35e-119">Em seguida, o cliente do teams emite novamente a consulta para o serviço, o que inclui o código de autenticação passado na etapa 5.</span><span class="sxs-lookup"><span data-stu-id="4e35e-119">The Teams client then reissues the query to your service, which includes the authentication code passed in step 5.</span></span>

<span data-ttu-id="4e35e-120">Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5.</span><span class="sxs-lookup"><span data-stu-id="4e35e-120">Your service should verify that the authentication code received in step 6 matches the one from step 5.</span></span> <span data-ttu-id="4e35e-121">Isso garante que um usuário mal-intencionado não tente falsificar ou comprometer o fluxo de entrada.</span><span class="sxs-lookup"><span data-stu-id="4e35e-121">This ensures that a malicious user does not try to spoof or compromise the sign-in flow.</span></span> <span data-ttu-id="4e35e-122">Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.</span><span class="sxs-lookup"><span data-stu-id="4e35e-122">This effectively "closes the loop" to finish the secure authentication sequence.</span></span>

### <a name="respond-with-a-sign-in-action"></a><span data-ttu-id="4e35e-123">Responder com uma ação de entrada</span><span class="sxs-lookup"><span data-stu-id="4e35e-123">Respond with a sign-in action</span></span>

<span data-ttu-id="4e35e-124">Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo `openUrl` que inclui a URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="4e35e-124">To prompt an unauthenticated user to sign in, respond with a suggested action of type `openUrl` that includes the authentication URL.</span></span>

#### <a name="response-example-for-a-sign-in-action"></a><span data-ttu-id="4e35e-125">Exemplo de resposta para uma ação de logon</span><span class="sxs-lookup"><span data-stu-id="4e35e-125">Response example for a sign-in action</span></span>

```json
{
  "composeExtension":{
    "type":"auth",
    "suggestedActions":{
      "actions":[
        {
          "type": "openUrl",
          "value": "https://example.com/auth",
          "title": "Sign in to this app"
        }
      ]
    }
  }
}
```

> [!NOTE]
> <span data-ttu-id="4e35e-126">Para que a experiência de entrada seja hospedada em um pop-up de equipes, a parte de domínio da URL deve estar na lista de domínios válidos de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e35e-126">For the sign-in experience to be hosted in a Teams pop-up, the domain portion of the URL must be in your app’s list of valid domains.</span></span> <span data-ttu-id="4e35e-127">(Consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.)</span><span class="sxs-lookup"><span data-stu-id="4e35e-127">(See [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema.)</span></span>

### <a name="start-the-sign-in-flow"></a><span data-ttu-id="4e35e-128">Iniciar o fluxo de entrada</span><span class="sxs-lookup"><span data-stu-id="4e35e-128">Start the sign-in flow</span></span>

<span data-ttu-id="4e35e-129">Sua experiência de entrada deve ser responsiva e ajustada em uma janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="4e35e-129">Your sign-in experience should be responsive and fit within a popup window.</span></span> <span data-ttu-id="4e35e-130">Ele deve se integrar ao [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client), que usa a transmissão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4e35e-130">It should integrate with the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client), which uses message passing.</span></span>

<span data-ttu-id="4e35e-131">Assim como ocorre com outras experiências incorporadas no Microsoft Teams, seu código dentro da janela precisa `microsoftTeams.initialize()`primeiro chamar.</span><span class="sxs-lookup"><span data-stu-id="4e35e-131">As with other embedded experiences running inside Microsoft Teams, your code inside the window needs to first call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="4e35e-132">Se o código executar um fluxo OAuth, você poderá passar a ID de usuário do teams para sua janela, o que pode passá-la para a URL de entrada OAuth.</span><span class="sxs-lookup"><span data-stu-id="4e35e-132">If your code performs an OAuth flow, you can pass the Teams user ID into your window, which then can pass it to the OAuth sign-in URL.</span></span>

### <a name="complete-the-sign-in-flow"></a><span data-ttu-id="4e35e-133">Concluir o fluxo de entrada</span><span class="sxs-lookup"><span data-stu-id="4e35e-133">Complete the sign-in flow</span></span>

<span data-ttu-id="4e35e-134">Quando a solicitação de entrada é concluída e redireciona de volta para sua página, ela deve executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="4e35e-134">When the sign-in request completes and redirects back to your page, it should perform the following steps:</span></span>

1. <span data-ttu-id="4e35e-135">Gere um código de segurança.</span><span class="sxs-lookup"><span data-stu-id="4e35e-135">Generate a security code.</span></span> <span data-ttu-id="4e35e-136">(Pode ser um número aleatório.) Você precisa armazenar em cache esse código em seu serviço, junto com as credenciais obtidas por meio do fluxo de entrada (como tokens OAuth 2,0).</span><span class="sxs-lookup"><span data-stu-id="4e35e-136">(This can be a random number.) You need to cache this code on your service, along with the credentials obtained through the sign-in flow (such as OAuth 2.0 tokens).</span></span>
2. <span data-ttu-id="4e35e-137">Chame `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.</span><span class="sxs-lookup"><span data-stu-id="4e35e-137">Call `microsoftTeams.authentication.notifySuccess` and pass the security code.</span></span>

<span data-ttu-id="4e35e-138">Neste ponto, a janela é fechada e o controle é passado para o cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="4e35e-138">At this point, the window closes and control is passed to the Teams client.</span></span> <span data-ttu-id="4e35e-139">Agora, o cliente pode reemitir a consulta de usuário original, juntamente com o código `state` de segurança na propriedade.</span><span class="sxs-lookup"><span data-stu-id="4e35e-139">The client now can reissue the original user query, along with the security code in the `state` property.</span></span> <span data-ttu-id="4e35e-140">Seu código pode usar o código de segurança para pesquisar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="4e35e-140">Your code can use the security code to look up the credentials stored earlier to complete the authentication sequence and then complete the user request.</span></span>

#### <a name="reissued-request-example"></a><span data-ttu-id="4e35e-141">Exemplo de solicitação reemitida</span><span class="sxs-lookup"><span data-stu-id="4e35e-141">Reissued request example</span></span>

```json
{
    "name": "composeExtension/query",
    "value": {
        "commandId": "insertWiki",
        "parameters": [{
            "name": "searchKeyword",
            "value": "lakers"
        }],
        "state": "12345",
        "queryOptions": {
            "skip": 0,
            "count": 25
        }
    },
    "type": "invoke",
    "timestamp": "2017-04-26T05:18:25.629Z",
    "localTimestamp": "2017-04-25T22:18:25.629-07:00",
    "entities": [{
        "locale": "en-US",
        "country": "US",
        "platform": "Web",
        "type": "clientInfo"
    }],
    "text": "",
    "attachments": [],
    "address": {
        "id": "f:7638210432489287768",
        "channelId": "msteams",
        "user": {
            "id": "29:1A5TJWHkbOwSyu_L9Ktk9QFI1d_kBOEPeNEeO1INscpKHzHTvWfiau5AX_6y3SuiOby-r73dzHJ17HipUWqGPgw",
            "aadObjectId": "fc8ca1c0-d043-4af6-b09f-141536207403"
        },
        "conversation": {
            "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
        },
        "bot": {
            "id": "28:c073afa8-7e77-4f92-b3e7-aa589e952a3e",
            "name": "maotestbot2"
        },
        "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
        "useAuth": true
    },
    "source": "msteams"
}
```

