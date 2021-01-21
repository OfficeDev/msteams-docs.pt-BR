---
title: Adicionar autenticação à extensão de mensagens
author: clearab
description: Como adicionar autenticação a uma extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 4ebe65af06240d13ceb99fe3b7640ab402d716c5
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911867"
---
# <a name="add-authentication-to-your-messaging-extension"></a><span data-ttu-id="418c3-103">Adicionar autenticação à extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="418c3-103">Add authentication to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a><span data-ttu-id="418c3-104">Identificar o usuário</span><span class="sxs-lookup"><span data-stu-id="418c3-104">Identify the user</span></span>

<span data-ttu-id="418c3-105">Todas as solicitações para seus serviços incluem a ID ofuscada do usuário que realizou a solicitação, bem como o nome de exibição do usuário e a ID de objeto do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="418c3-105">Every request to your services includes the obfuscated ID of the user that performed the request, as well as the user's display name and Azure Active Directory object ID.</span></span>

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

<span data-ttu-id="418c3-106">Os `id` valores e os valores são `aadObjectId` garantidos como sendo os do usuário autenticado do Teams.</span><span class="sxs-lookup"><span data-stu-id="418c3-106">The `id` and `aadObjectId` values are guaranteed to be that of the authenticated Teams user.</span></span> <span data-ttu-id="418c3-107">Eles podem ser usados como chaves para procurar credenciais ou qualquer estado armazenado em cache em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="418c3-107">They can be used as keys to look up credentials or any cached state in your service.</span></span> <span data-ttu-id="418c3-108">Além disso, cada solicitação contém a ID de locatário do Azure Active Directory do usuário, que pode ser usada para identificar a organização do usuário.</span><span class="sxs-lookup"><span data-stu-id="418c3-108">In addition, each request contains the Azure Active Directory tenant ID of the user, which can be used to identify the user’s organization.</span></span> <span data-ttu-id="418c3-109">Se aplicável, a solicitação também contém as IDs de equipe e de canal da qual a solicitação se originou.</span><span class="sxs-lookup"><span data-stu-id="418c3-109">If applicable, the request also contains the team and channel IDs from which the request originated.</span></span>

## <a name="authentication"></a><span data-ttu-id="418c3-110">Autenticação</span><span class="sxs-lookup"><span data-stu-id="418c3-110">Authentication</span></span>

<span data-ttu-id="418c3-111">Se o serviço exigir autenticação do usuário, você precisará entrar no usuário antes que ele possa usar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="418c3-111">If your service requires user authentication, you need to sign in the user before he or she can use the messaging extension.</span></span> <span data-ttu-id="418c3-112">Se você tiver escrito um bot ou uma guia que entre no usuário, esta seção deve ser familiar.</span><span class="sxs-lookup"><span data-stu-id="418c3-112">If you have written a bot or a tab that signs in the user, this section should be familiar.</span></span>

<span data-ttu-id="418c3-113">A sequência é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="418c3-113">The sequence is as follows:</span></span>

1. <span data-ttu-id="418c3-114">O usuário emite uma consulta ou a consulta padrão é automaticamente enviada ao serviço.</span><span class="sxs-lookup"><span data-stu-id="418c3-114">User issues a query, or the default query is automatically sent to your service.</span></span>
2. <span data-ttu-id="418c3-115">Seu serviço verifica se o usuário foi autenticado primeiro inspecionando a ID de usuário do Teams.</span><span class="sxs-lookup"><span data-stu-id="418c3-115">Your service checks whether the user has first authenticated by inspecting the Teams user ID.</span></span>
3. <span data-ttu-id="418c3-116">Se o usuário não tiver sido autenticado, envie uma resposta `auth` com uma `openUrl` ação sugerida, incluindo a URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="418c3-116">If the user has not authenticated, send back an `auth` response with an `openUrl` suggested action including the authentication URL.</span></span>
4. <span data-ttu-id="418c3-117">O cliente Microsoft Teams inicia uma janela pop-up hospedando sua página da Web usando a URL de autenticação determinada.</span><span class="sxs-lookup"><span data-stu-id="418c3-117">The Microsoft Teams client launches a pop-up window hosting your webpage using the given authentication URL.</span></span>
5. <span data-ttu-id="418c3-118">Depois que o usuário entrar, você deverá fechar a janela e enviar um "código de autenticação" para o cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="418c3-118">After the user signs in, you should close your window and send an "authentication code" to the Teams client.</span></span>
6. <span data-ttu-id="418c3-119">Em seguida, o cliente do Teams em seguida emira a consulta para seu serviço, o que inclui o código de autenticação passado na etapa 5.</span><span class="sxs-lookup"><span data-stu-id="418c3-119">The Teams client then reissues the query to your service, which includes the authentication code passed in step 5.</span></span>

<span data-ttu-id="418c3-120">Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5.</span><span class="sxs-lookup"><span data-stu-id="418c3-120">Your service should verify that the authentication code received in step 6 matches the one from step 5.</span></span> <span data-ttu-id="418c3-121">Isso garante que um usuário mal-intencionado não tente fazer spoof ou comprometer o fluxo de login.</span><span class="sxs-lookup"><span data-stu-id="418c3-121">This ensures that a malicious user does not try to spoof or compromise the sign-in flow.</span></span> <span data-ttu-id="418c3-122">Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.</span><span class="sxs-lookup"><span data-stu-id="418c3-122">This effectively "closes the loop" to finish the secure authentication sequence.</span></span>

### <a name="respond-with-a-sign-in-action"></a><span data-ttu-id="418c3-123">Responder com uma ação de login</span><span class="sxs-lookup"><span data-stu-id="418c3-123">Respond with a sign-in action</span></span>

<span data-ttu-id="418c3-124">Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo que inclui a `openUrl` URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="418c3-124">To prompt an unauthenticated user to sign in, respond with a suggested action of type `openUrl` that includes the authentication URL.</span></span>

#### <a name="response-example-for-a-sign-in-action"></a><span data-ttu-id="418c3-125">Exemplo de resposta para uma ação de login</span><span class="sxs-lookup"><span data-stu-id="418c3-125">Response example for a sign-in action</span></span>

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
> <span data-ttu-id="418c3-126">Para que a experiência de login seja hospedada em um pop-up do Teams, a parte de domínio da URL deve estar na lista de domínios válidos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="418c3-126">For the sign-in experience to be hosted in a Teams pop-up, the domain portion of the URL must be in your app’s list of valid domains.</span></span> <span data-ttu-id="418c3-127">(Consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.)</span><span class="sxs-lookup"><span data-stu-id="418c3-127">(See [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema.)</span></span>

### <a name="start-the-sign-in-flow"></a><span data-ttu-id="418c3-128">Iniciar o fluxo de login</span><span class="sxs-lookup"><span data-stu-id="418c3-128">Start the sign-in flow</span></span>

<span data-ttu-id="418c3-129">Sua experiência de login deve ser responsiva e caber em uma janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="418c3-129">Your sign-in experience should be responsive and fit within a popup window.</span></span> <span data-ttu-id="418c3-130">Ele deve se integrar ao [SDK](/javascript/api/overview/msteams-client)do cliente JavaScript do Microsoft Teams, que usa a passagem de mensagens.</span><span class="sxs-lookup"><span data-stu-id="418c3-130">It should integrate with the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client), which uses message passing.</span></span>

<span data-ttu-id="418c3-131">Assim como outras experiências incorporadas em execução no Microsoft Teams, seu código dentro da janela precisa primeiro `microsoftTeams.initialize()` chamar.</span><span class="sxs-lookup"><span data-stu-id="418c3-131">As with other embedded experiences running inside Microsoft Teams, your code inside the window needs to first call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="418c3-132">Se o código executar um fluxo OAuth, você poderá passar a ID de usuário do Teams para sua janela, que pode passá-la para a URL de entrada do OAuth.</span><span class="sxs-lookup"><span data-stu-id="418c3-132">If your code performs an OAuth flow, you can pass the Teams user ID into your window, which then can pass it to the OAuth sign-in URL.</span></span>

### <a name="complete-the-sign-in-flow"></a><span data-ttu-id="418c3-133">Concluir o fluxo de login</span><span class="sxs-lookup"><span data-stu-id="418c3-133">Complete the sign-in flow</span></span>

<span data-ttu-id="418c3-134">Quando a solicitação de login for concluída e redirecionada de volta para sua página, ela deverá executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="418c3-134">When the sign-in request completes and redirects back to your page, it should perform the following steps:</span></span>

1. <span data-ttu-id="418c3-135">Gere um código de segurança.</span><span class="sxs-lookup"><span data-stu-id="418c3-135">Generate a security code.</span></span> <span data-ttu-id="418c3-136">(Pode ser um número aleatório.) Você precisa armazenar em cache esse código em seu serviço, juntamente com as credenciais obtidas por meio do fluxo de logon (como tokens OAuth 2.0).</span><span class="sxs-lookup"><span data-stu-id="418c3-136">(This can be a random number.) You need to cache this code on your service, along with the credentials obtained through the sign-in flow (such as OAuth 2.0 tokens).</span></span>
2. <span data-ttu-id="418c3-137">Ligue `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.</span><span class="sxs-lookup"><span data-stu-id="418c3-137">Call `microsoftTeams.authentication.notifySuccess` and pass the security code.</span></span>

<span data-ttu-id="418c3-138">Neste ponto, a janela é fechada e o controle é passado para o cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="418c3-138">At this point, the window closes and control is passed to the Teams client.</span></span> <span data-ttu-id="418c3-139">O cliente agora pode reemarciar a consulta do usuário original, juntamente com o código de segurança na `state` propriedade.</span><span class="sxs-lookup"><span data-stu-id="418c3-139">The client now can reissue the original user query, along with the security code in the `state` property.</span></span> <span data-ttu-id="418c3-140">Seu código pode usar o código de segurança para procurar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="418c3-140">Your code can use the security code to look up the credentials stored earlier to complete the authentication sequence and then complete the user request.</span></span>

#### <a name="reissued-request-example"></a><span data-ttu-id="418c3-141">Exemplo de solicitação em reemissão</span><span class="sxs-lookup"><span data-stu-id="418c3-141">Reissued request example</span></span>

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

## <a name="samples"></a><span data-ttu-id="418c3-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="418c3-142">Samples</span></span>
<span data-ttu-id="418c3-143">Para código de exemplo mostrando o processo de autenticação messaging-extensions, consulte:</span><span class="sxs-lookup"><span data-stu-id="418c3-143">For sample code showing the messaging-extensions authentication process, see:</span></span>

[<span data-ttu-id="418c3-144">Exemplo de autenticação de extensões de mensagens do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="418c3-144">Microsoft Teams messaging-extensions authentication sample</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)

 
