---
title: Adicionar autenticação à sua extensão de mensagens
author: clearab
description: Como adicionar autenticação a uma extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 04ece6fe6f5e824873ed6e69385bce017df6927d
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696770"
---
# <a name="add-authentication-to-your-messaging-extension"></a><span data-ttu-id="33daa-103">Adicionar autenticação à sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="33daa-103">Add authentication to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a><span data-ttu-id="33daa-104">Identificar o usuário</span><span class="sxs-lookup"><span data-stu-id="33daa-104">Identify the user</span></span>

<span data-ttu-id="33daa-105">Todas as solicitações aos seus serviços incluem a ID do usuário, o nome de exibição do usuário e a ID do objeto do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="33daa-105">Every request to your services includes the user  ID, the user's display name and Azure Active Directory object ID.</span></span>

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

<span data-ttu-id="33daa-106">Os `id` valores e são `aadObjectId` garantidos para o usuário autenticado do Teams.</span><span class="sxs-lookup"><span data-stu-id="33daa-106">The `id` and `aadObjectId` values are guaranteed for the authenticated Teams user.</span></span> <span data-ttu-id="33daa-107">Eles são usados como chaves para procurar as credenciais ou qualquer estado armazenado em cache em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="33daa-107">They are used as keys to look up the credentials or any cached state in your service.</span></span> <span data-ttu-id="33daa-108">Além disso, cada solicitação contém a ID de locatário do Azure Active Directory do usuário, que é usada para identificar a organização do usuário.</span><span class="sxs-lookup"><span data-stu-id="33daa-108">In addition, each request contains the Azure Active Directory tenant ID of the user, which is used to identify the user’s organization.</span></span> <span data-ttu-id="33daa-109">Se aplicável, a solicitação também contém a ID de equipe e a ID do canal da qual a solicitação é originada.</span><span class="sxs-lookup"><span data-stu-id="33daa-109">If applicable, the request also contains the team Id and channel ID from which the request is originated.</span></span>

## <a name="authentication"></a><span data-ttu-id="33daa-110">Autenticação</span><span class="sxs-lookup"><span data-stu-id="33daa-110">Authentication</span></span>

<span data-ttu-id="33daa-111">Se o serviço exigir autenticação do usuário, os usuários devem entrar antes de usar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="33daa-111">If your service requires user authentication, the users must sign in before they use the messaging extension.</span></span> <span data-ttu-id="33daa-112">As etapas de autenticação são semelhantes às de um bot ou guia. A sequência é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="33daa-112">The authentication steps are similar to that of a bot or tab. The sequence is as follows:</span></span>

1. <span data-ttu-id="33daa-113">O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="33daa-113">User issues a query, or the default query is automatically sent to your service.</span></span>
1. <span data-ttu-id="33daa-114">Seu serviço verifica se o usuário é autenticado inspecionando a ID do usuário do Teams.</span><span class="sxs-lookup"><span data-stu-id="33daa-114">Your service checks whether the user is authenticated by inspecting the Teams user ID.</span></span>
1. <span data-ttu-id="33daa-115">Se o usuário não for autenticado, envie uma resposta `auth` com uma `openUrl` ação sugerida, incluindo a URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="33daa-115">If the user is not authenticated, send back an `auth` response with an `openUrl` suggested action including the authentication URL.</span></span>
1. <span data-ttu-id="33daa-116">O cliente do Microsoft Teams inicia uma caixa de diálogo hospedando sua página da Web usando a URL de autenticação determinada.</span><span class="sxs-lookup"><span data-stu-id="33daa-116">The Microsoft Teams client launches a dialog box hosting your webpage using the given authentication URL.</span></span>
1. <span data-ttu-id="33daa-117">Depois que o usuário entrar, você deve fechar a janela e enviar um código de **autenticação** para o cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="33daa-117">After the user signs in, you should close your window and send an **authentication code** to the Teams client.</span></span>
1. <span data-ttu-id="33daa-118">Em seguida, o cliente do Teams reenvia a consulta ao seu serviço, que inclui o código de autenticação passado na Etapa 5.</span><span class="sxs-lookup"><span data-stu-id="33daa-118">The Teams client then reissues the query to your service, which includes the authentication code passed in Step 5.</span></span>

<span data-ttu-id="33daa-119">Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5.</span><span class="sxs-lookup"><span data-stu-id="33daa-119">Your service should verify that the authentication code received in step 6 matches the one from step 5.</span></span> <span data-ttu-id="33daa-120">Isso garante que um usuário mal-intencionado não tente fazer a spoof ou comprometer o fluxo de login.</span><span class="sxs-lookup"><span data-stu-id="33daa-120">This ensures that a malicious user does not try to spoof or compromise the sign in flow.</span></span> <span data-ttu-id="33daa-121">Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.</span><span class="sxs-lookup"><span data-stu-id="33daa-121">This effectively "closes the loop" to finish the secure authentication sequence.</span></span>

### <a name="respond-with-a-sign-in-action"></a><span data-ttu-id="33daa-122">Responder com uma ação de login</span><span class="sxs-lookup"><span data-stu-id="33daa-122">Respond with a sign-in action</span></span>

<span data-ttu-id="33daa-123">Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo que inclui a `openUrl` URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="33daa-123">To prompt an unauthenticated user to sign in, respond with a suggested action of type `openUrl` that includes the authentication URL.</span></span>

#### <a name="response-example-for-a-sign-in-action"></a><span data-ttu-id="33daa-124">Exemplo de resposta para uma ação de login</span><span class="sxs-lookup"><span data-stu-id="33daa-124">Response example for a sign-in action</span></span>

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
> <span data-ttu-id="33daa-125">Para que a experiência de login seja hospedada em uma janela pop-up do Teams, a parte de domínio da URL deve estar na lista de domínios válidos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33daa-125">For the sign in experience to be hosted in a Teams pop-up window, the domain portion of the URL must be in your app’s list of valid domains.</span></span> <span data-ttu-id="33daa-126">Para obter mais informações, [consulte validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.</span><span class="sxs-lookup"><span data-stu-id="33daa-126">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema.</span></span>

### <a name="start-the-sign-in-flow"></a><span data-ttu-id="33daa-127">Iniciar o fluxo de login</span><span class="sxs-lookup"><span data-stu-id="33daa-127">Start the sign in flow</span></span>

<span data-ttu-id="33daa-128">Sua experiência de login deve ser responsiva e adequada dentro de uma janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="33daa-128">Your sign in experience must be responsive and fit within a pop-up window.</span></span> <span data-ttu-id="33daa-129">Ele deve se integrar ao [SDK do cliente JavaScript do Microsoft Teams,](/javascript/api/overview/msteams-client)que usa a passagem de mensagens.</span><span class="sxs-lookup"><span data-stu-id="33daa-129">It should integrate with the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client), which uses message passing.</span></span>

<span data-ttu-id="33daa-130">Assim como com outras experiências incorporadas em execução no Microsoft Teams, seu código dentro da janela precisa chamar primeiro `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="33daa-130">As with other embedded experiences running inside Microsoft Teams, your code inside the window needs to first call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="33daa-131">Se seu código executar um fluxo OAuth, você poderá passar a ID do usuário do Teams para sua janela, que, em seguida, passa-a para a URL de entrada do OAuth.</span><span class="sxs-lookup"><span data-stu-id="33daa-131">If your code performs an OAuth flow, you can pass the Teams user ID into your window, which then passes it to the OAuth sign-in URL.</span></span>

### <a name="complete-the-sign-in-flow"></a><span data-ttu-id="33daa-132">Concluir o fluxo de login</span><span class="sxs-lookup"><span data-stu-id="33daa-132">Complete the sign in flow</span></span>

<span data-ttu-id="33daa-133">Quando a solicitação de entrar é concluída e redireciona de volta para sua página, ela deve executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="33daa-133">When the sign in request completes and redirects back to your page, it must perform the following steps:</span></span>

1. <span data-ttu-id="33daa-134">Gere um código de segurança.</span><span class="sxs-lookup"><span data-stu-id="33daa-134">Generate a security code.</span></span> <span data-ttu-id="33daa-135">Esse é um número aleatório.</span><span class="sxs-lookup"><span data-stu-id="33daa-135">This is a random number.</span></span> <span data-ttu-id="33daa-136">Você deve armazenar em cache esse código em seu serviço, juntamente com as credenciais obtidas por meio do fluxo de logon, como tokens OAuth 2.0.</span><span class="sxs-lookup"><span data-stu-id="33daa-136">You must cache this code on your service, along with the credentials obtained through the sign in flow, such as OAuth 2.0 tokens.</span></span>
1. <span data-ttu-id="33daa-137">Chame `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.</span><span class="sxs-lookup"><span data-stu-id="33daa-137">Call `microsoftTeams.authentication.notifySuccess` and pass the security code.</span></span>

<span data-ttu-id="33daa-138">Neste ponto, a janela fecha e o controle é passado para o cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="33daa-138">At this point, the window closes and control is passed to the Teams client.</span></span> <span data-ttu-id="33daa-139">O cliente agora reeditará a consulta de usuário original, juntamente com o código de segurança na `state` propriedade.</span><span class="sxs-lookup"><span data-stu-id="33daa-139">The client now reissues the original user query, along with the security code in the `state` property.</span></span> <span data-ttu-id="33daa-140">Seu código pode usar o código de segurança para procurar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="33daa-140">Your code can use the security code to look up the credentials stored earlier to complete the authentication sequence and then complete the user request.</span></span>

#### <a name="reissued-request-example"></a><span data-ttu-id="33daa-141">Exemplo de solicitação reemissão</span><span class="sxs-lookup"><span data-stu-id="33daa-141">Reissued request example</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="33daa-142">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="33daa-142">Code sample</span></span>
|<span data-ttu-id="33daa-143">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="33daa-143">**Sample name**</span></span> | <span data-ttu-id="33daa-144">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="33daa-144">**Description**</span></span> |<span data-ttu-id="33daa-145">**.NET**</span><span class="sxs-lookup"><span data-stu-id="33daa-145">**.NET**</span></span> | <span data-ttu-id="33daa-146">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="33daa-146">**Node.js**</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="33daa-147">Extensões de mensagens - auth e config</span><span class="sxs-lookup"><span data-stu-id="33daa-147">Messaging extensions - auth and config</span></span> | <span data-ttu-id="33daa-148">Uma Extensão de Mensagens que tem uma página de configuração, aceita solicitações de pesquisa e retorna resultados depois que o usuário se inscreveu.</span><span class="sxs-lookup"><span data-stu-id="33daa-148">A Messaging Extension that has a configuration page, accepts search requests, and returns results after the user has signed in.</span></span> |[<span data-ttu-id="33daa-149">View</span><span class="sxs-lookup"><span data-stu-id="33daa-149">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)|[<span data-ttu-id="33daa-150">View</span><span class="sxs-lookup"><span data-stu-id="33daa-150">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)| 

 
