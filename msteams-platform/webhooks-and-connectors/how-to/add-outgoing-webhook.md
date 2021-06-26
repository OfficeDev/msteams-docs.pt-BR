---
title: Criar um Webhook de Saída
author: laujan
description: descreve como criar um Webhook de Saída
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
keywords: guias do teams webhook de saída mensagem ativas verificar webhook
ms.openlocfilehash: c02ff5388e47ba40056afcc1fcf5e8d7ad4437e8
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140317"
---
# <a name="create-outgoing-webhook"></a><span data-ttu-id="0e4db-104">Criar Webhook de saída</span><span class="sxs-lookup"><span data-stu-id="0e4db-104">Create Outgoing Webhook</span></span>

<span data-ttu-id="0e4db-105">O Webhook de saída age como um bot e pesquisa mensagens em canais usando **@mention**.</span><span class="sxs-lookup"><span data-stu-id="0e4db-105">The Outgoing Webhook acts as a bot and search for messages in channels using **@mention**.</span></span> <span data-ttu-id="0e4db-106">Ele envia notificações para serviços Web externos e responde com mensagens ricas, que incluem cartões e imagens.</span><span class="sxs-lookup"><span data-stu-id="0e4db-106">It sends notifications to external web services and responds with rich messages, which include cards and images.</span></span> <span data-ttu-id="0e4db-107">Ele ajuda a ignorar o processo de criação de bots por meio do [Microsoft Bot Framework](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="0e4db-107">It helps to skip the process of creating bots through the [Microsoft Bot Framework](https://dev.botframework.com/).</span></span>

## <a name="key-features-of-outgoing-webhook"></a><span data-ttu-id="0e4db-108">Principais recursos do Webhook de Saída</span><span class="sxs-lookup"><span data-stu-id="0e4db-108">Key features of Outgoing Webhook</span></span>

<span data-ttu-id="0e4db-109">A tabela a seguir fornece os recursos e a descrição dos Webhooks de saída:</span><span class="sxs-lookup"><span data-stu-id="0e4db-109">The following table provides the features and description of Outgoing Webhooks:</span></span>

| <span data-ttu-id="0e4db-110">Recursos</span><span class="sxs-lookup"><span data-stu-id="0e4db-110">Features</span></span> | <span data-ttu-id="0e4db-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e4db-111">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="0e4db-112">Configuração com escopo</span><span class="sxs-lookup"><span data-stu-id="0e4db-112">Scoped configuration</span></span>| <span data-ttu-id="0e4db-113">Os webhooks têm escopo no nível da equipe.</span><span class="sxs-lookup"><span data-stu-id="0e4db-113">Webhooks are scoped at the team level.</span></span> <span data-ttu-id="0e4db-114">O processo de configuração obrigatório para cada um adiciona um Webhook de saída.</span><span class="sxs-lookup"><span data-stu-id="0e4db-114">Mandatory set up process for each adds an Outgoing Webhook.</span></span> |
| <span data-ttu-id="0e4db-115">Mensagens reativas</span><span class="sxs-lookup"><span data-stu-id="0e4db-115">Reactive messaging</span></span>| <span data-ttu-id="0e4db-116">Os usuários devem usar @mention webhook para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="0e4db-116">Users must use @mention for the webhook to receive messages.</span></span> <span data-ttu-id="0e4db-117">Atualmente, os usuários só podem enviar um Webhook de Saída em canais públicos e não no escopo pessoal ou privado.</span><span class="sxs-lookup"><span data-stu-id="0e4db-117">Currently, users can only message an Outgoing Webhook in public channels and not within the personal or private scope.</span></span> |
|<span data-ttu-id="0e4db-118">Troca de mensagens HTTP padrão</span><span class="sxs-lookup"><span data-stu-id="0e4db-118">Standard HTTP message exchange</span></span>|<span data-ttu-id="0e4db-119">As respostas aparecem na mesma cadeia que a mensagem de solicitação original e podem incluir qualquer conteúdo de mensagem da Estrutura de Bot, por exemplo, texto rico, imagens, cartões e emojis.</span><span class="sxs-lookup"><span data-stu-id="0e4db-119">Responses appear in the same chain as the original request message and can include any Bot Framework message content, for example, rich text, images, cards, and emojis.</span></span> <span data-ttu-id="0e4db-120">Embora os Webhooks de saída possam usar cartões, eles não podem usar nenhuma ação de cartão, exceto `openURL` por .</span><span class="sxs-lookup"><span data-stu-id="0e4db-120">Although Outgoing Webhooks can use cards, they cannot use any card actions except for `openURL`.</span></span>|
| <span data-ttu-id="0e4db-121">Teams Suporte ao método API</span><span class="sxs-lookup"><span data-stu-id="0e4db-121">Teams API method support</span></span>|<span data-ttu-id="0e4db-122">Webhooks de saída envia um HTTP POST para um serviço Web e obtém uma resposta.</span><span class="sxs-lookup"><span data-stu-id="0e4db-122">Outgoing Webhooks sends an HTTP POST to a web service and gets a response.</span></span> <span data-ttu-id="0e4db-123">Eles não podem acessar outras APIs, como recuperar a lista ou a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="0e4db-123">They cannot access any other APIs, such as retrieve the roster or list of channels in a team.</span></span>|

## <a name="create-outgoing-webhooks"></a><span data-ttu-id="0e4db-124">Criar Webhooks de saída</span><span class="sxs-lookup"><span data-stu-id="0e4db-124">Create Outgoing Webhooks</span></span>

<span data-ttu-id="0e4db-125">Crie Webhooks de saída e adicione bots personalizados Teams.</span><span class="sxs-lookup"><span data-stu-id="0e4db-125">Create Outgoing Webhooks and add custom bots to Teams.</span></span>

<span data-ttu-id="0e4db-126">**Para criar um Webhook de Saída**</span><span class="sxs-lookup"><span data-stu-id="0e4db-126">**To create an Outgoing Webhook**</span></span>

1. <span data-ttu-id="0e4db-127">Selecione **Teams** no painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="0e4db-127">Select **Teams** from the left pane.</span></span> <span data-ttu-id="0e4db-128">A **Teams** página é exibida:</span><span class="sxs-lookup"><span data-stu-id="0e4db-128">The **Teams** page appears:</span></span>

    ![Canal do Teams](~/assets/images/teamschannel.png)

1. <span data-ttu-id="0e4db-130">Na página **Teams,** selecione a equipe necessária para criar um Webhook de saída e selecione o &#8226;&#8226;&#8226;.</span><span class="sxs-lookup"><span data-stu-id="0e4db-130">In the **Teams** page, select the required team to create an Outgoing Webhook and select the &#8226;&#8226;&#8226;.</span></span> <span data-ttu-id="0e4db-131">No menu suspenso, selecione **Gerenciar equipe**:</span><span class="sxs-lookup"><span data-stu-id="0e4db-131">In the dropdown menu, select **Manage team**:</span></span>

    ![Criar Webhook de saída](~/assets/images/outgoingwebhook1.png)

1. <span data-ttu-id="0e4db-133">Selecione a **guia Aplicativos** na página do canal:</span><span class="sxs-lookup"><span data-stu-id="0e4db-133">Select the **Apps** tab on the channel page:</span></span>

    ![Criar um Webhook de Saída](~/assets/images/outgoingwebhook2.png)

1. <span data-ttu-id="0e4db-135">Selecione **Criar um Webhook de Saída:**</span><span class="sxs-lookup"><span data-stu-id="0e4db-135">Select **Create an Outgoing Webhook**:</span></span>

    ![Criar Webhooks de saída](~/assets/images/outgoingwebhook3.png)

1. <span data-ttu-id="0e4db-137">Digite os seguintes detalhes na página **Criar um Webhook de** Saída:</span><span class="sxs-lookup"><span data-stu-id="0e4db-137">Type the following details in the **Create an Outgoing Webhook** page:</span></span>

    * <span data-ttu-id="0e4db-138">**Nome**: o título de webhook e @mention guia.</span><span class="sxs-lookup"><span data-stu-id="0e4db-138">**Name**: The webhook title and @mention tab.</span></span>
    * <span data-ttu-id="0e4db-139">**URL de retorno** de chamada : o ponto de extremidade HTTPS que aceita cargas JSON e recebe solicitações POST de Teams.</span><span class="sxs-lookup"><span data-stu-id="0e4db-139">**Callback URL**: The HTTPS endpoint that accepts JSON payloads and receives POST requests from Teams.</span></span>
    * <span data-ttu-id="0e4db-140">**Descrição**: uma cadeia de caracteres detalhada que aparece no cartão de perfil e no painel de aplicativos no nível da equipe.</span><span class="sxs-lookup"><span data-stu-id="0e4db-140">**Description**: A detailed string that appears in the profile card and the team-level App dashboard.</span></span>
    * <span data-ttu-id="0e4db-141">**Imagem do** perfil : um ícone de aplicativo para seu webhook, que é opcional.</span><span class="sxs-lookup"><span data-stu-id="0e4db-141">**Profile Picture**: An app icon for your webhook, which is optional.</span></span>

1. <span data-ttu-id="0e4db-142">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="0e4db-142">Select **Create**.</span></span> <span data-ttu-id="0e4db-143">O Webhook de saída é adicionado ao canal atual da equipe:</span><span class="sxs-lookup"><span data-stu-id="0e4db-143">The Outgoing Webhook is added to the current team's channel:</span></span>

    ![criar Webhook de saída](~/assets/images/outgoingwebhook.png)

<span data-ttu-id="0e4db-145">Uma [caixa de diálogo HMAC (Código](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) de Autenticação de Mensagem baseado em hash) é exibida.</span><span class="sxs-lookup"><span data-stu-id="0e4db-145">A [Hash-based Message Authentication Code (HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) dialogue box appears.</span></span> <span data-ttu-id="0e4db-146">É um token de segurança usado para autenticar chamadas entre Teams e o serviço externo designado.</span><span class="sxs-lookup"><span data-stu-id="0e4db-146">It is a security token used to authenticate calls between Teams and the designated outside service.</span></span>

>[!NOTE]
> <span data-ttu-id="0e4db-147">O Webhook de Saída está disponível para os usuários da equipe, somente se a URL for válida e os tokens de autenticação do servidor e do cliente são iguais.</span><span class="sxs-lookup"><span data-stu-id="0e4db-147">The Outgoing Webhook is available to the team's users, only if the URL is valid and the server and client authentication tokens are equal.</span></span> <span data-ttu-id="0e4db-148">Por exemplo, um handshake HMAC.</span><span class="sxs-lookup"><span data-stu-id="0e4db-148">For example, an HMAC handshake.</span></span>

<span data-ttu-id="0e4db-149">O cenário a seguir fornece os detalhes para adicionar um Webhook de saída:</span><span class="sxs-lookup"><span data-stu-id="0e4db-149">The following scenario provides the details to add an Outgoing Webhook:</span></span>

* <span data-ttu-id="0e4db-150">Cenário: Push change status notifications on a Teams channel database server to your app.</span><span class="sxs-lookup"><span data-stu-id="0e4db-150">Scenario: Push change status notifications on a Teams channel database server to your app.</span></span>
* <span data-ttu-id="0e4db-151">Exemplo: você tem um aplicativo de linha de negócios que rastreia todas as operações CRUD, como criar, ler, atualizar e excluir.</span><span class="sxs-lookup"><span data-stu-id="0e4db-151">Example: You have a line of business app that tracks all CRUD operations, such as create, read, update, and delete.</span></span> <span data-ttu-id="0e4db-152">Essas operações são feitas nos registros dos funcionários por usuários de RH Teams canal em um Office 365 de terceiros.</span><span class="sxs-lookup"><span data-stu-id="0e4db-152">These operations are made to the employee records by Teams channel HR users across an Office 365 tenancy.</span></span>

# <a name="url-json-payload"></a>[<span data-ttu-id="0e4db-153">Carga JSON de URL</span><span class="sxs-lookup"><span data-stu-id="0e4db-153">URL JSON payload</span></span>](#tab/urljsonpayload)
<span data-ttu-id="0e4db-154">**Crie uma URL no servidor do aplicativo para aceitar e processar uma solicitação POST com uma carga JSON**</span><span class="sxs-lookup"><span data-stu-id="0e4db-154">**Create a URL on your app's server to accept and process a POST request with a JSON payload**</span></span>

<span data-ttu-id="0e4db-155">Seu serviço recebe mensagens em um esquema de mensagens de serviço de bot padrão do Azure.</span><span class="sxs-lookup"><span data-stu-id="0e4db-155">Your service receives messages in a standard Azure bot service messaging schema.</span></span> <span data-ttu-id="0e4db-156">O conector da Estrutura de Bots é um serviço RESTful que permite processar o intercâmbio de mensagens formatadas JSON por meio de protocolos HTTPS, conforme documentado na API de Serviço de Bot do [Azure.](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)</span><span class="sxs-lookup"><span data-stu-id="0e4db-156">The Bot Framework connector is a RESTful service that empowers to process the interchange of JSON formatted messages through HTTPS protocols as documented in the [Azure Bot Service API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).</span></span> <span data-ttu-id="0e4db-157">Como alternativa, você pode seguir o Microsoft Bot Framework SDK para processar e analisar mensagens.</span><span class="sxs-lookup"><span data-stu-id="0e4db-157">Alternatively, you can follow the Microsoft Bot Framework SDK to process and parse messages.</span></span> <span data-ttu-id="0e4db-158">Para obter mais informações, consulte [overview of Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).</span><span class="sxs-lookup"><span data-stu-id="0e4db-158">For more information, see [overview of Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).</span></span>

<span data-ttu-id="0e4db-159">Os Webhooks de saída são limitados ao `team` nível e ficam visíveis para todos os membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="0e4db-159">Outgoing Webhooks are scoped to the `team` level and are visible to all the team members.</span></span> <span data-ttu-id="0e4db-160">Os usuários precisam **\@ mencionar** o nome do Webhook de Saída para invocá-lo no canal.</span><span class="sxs-lookup"><span data-stu-id="0e4db-160">Users need to **\@mention** the name of the Outgoing Webhook to invoke it in the channel.</span></span>

# <a name="verify-hmac-token"></a>[<span data-ttu-id="0e4db-161">Verificar token HMAC</span><span class="sxs-lookup"><span data-stu-id="0e4db-161">Verify HMAC token</span></span>](#tab/verifyhmactoken)
<span data-ttu-id="0e4db-162">**Criar um método para verificar o token HMAC do Webhook de Saída**</span><span class="sxs-lookup"><span data-stu-id="0e4db-162">**Create a method to verify the Outgoing Webhook HMAC token**</span></span>

<span data-ttu-id="0e4db-163">Usando exemplo de mensagem de entrada e ID: "contoso" de SigningKeyDictionary de {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.</span><span class="sxs-lookup"><span data-stu-id="0e4db-163">Using example of inbound message and ID: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.</span></span>

<span data-ttu-id="0e4db-164">Use o valor "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" na autorização do header de solicitação.</span><span class="sxs-lookup"><span data-stu-id="0e4db-164">Use the value "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in the authorization of request header.</span></span>

<span data-ttu-id="0e4db-165">Para garantir que seu serviço receba chamadas somente de clientes Teams reais, o Teams fornece um código HMAC no cabeçalho de autorização `hmac` HTTP.</span><span class="sxs-lookup"><span data-stu-id="0e4db-165">To ensure that your service is receiving calls only from actual Teams clients, Teams provides an HMAC code in the HTTP `hmac` authorization header.</span></span> <span data-ttu-id="0e4db-166">Sempre inclua o código em seu protocolo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="0e4db-166">Always include the code in your authentication protocol.</span></span>

<span data-ttu-id="0e4db-167">Seu código deve sempre validar a assinatura HMAC incluída na solicitação da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0e4db-167">Your code must always validate the HMAC signature included in the request as follows:</span></span>

* <span data-ttu-id="0e4db-168">Gere o token HMAC do corpo da solicitação da mensagem.</span><span class="sxs-lookup"><span data-stu-id="0e4db-168">Generate the HMAC token from the request body of the message.</span></span> <span data-ttu-id="0e4db-169">Há bibliotecas padrão para fazer isso na maioria das plataformas, como [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js e [Teams webhook](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) para C \# ).</span><span class="sxs-lookup"><span data-stu-id="0e4db-169">There are standard libraries to do this on most platform, such as [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js and [Teams webhook sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C\#).</span></span> <span data-ttu-id="0e4db-170">Microsoft Teams usa criptografia HMAC SHA256 padrão.</span><span class="sxs-lookup"><span data-stu-id="0e4db-170">Microsoft Teams uses standard SHA256 HMAC cryptography.</span></span> <span data-ttu-id="0e4db-171">Você deve converter o corpo em uma matriz de byte em UTF8.</span><span class="sxs-lookup"><span data-stu-id="0e4db-171">You must convert the body to a byte array in UTF8.</span></span>
* <span data-ttu-id="0e4db-172">Calcule o hash da matriz de byte do token de segurança fornecido pelo Teams quando você registrou o Webhook de Saída no cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="0e4db-172">Compute the hash from the byte array of the security token provided by Teams when you registered the Outgoing Webhook in the Teams client.</span></span> <span data-ttu-id="0e4db-173">Consulte [create an Outgoing Webhook](#create-outgoing-webhook).</span><span class="sxs-lookup"><span data-stu-id="0e4db-173">See [create an Outgoing Webhook](#create-outgoing-webhook).</span></span>
* <span data-ttu-id="0e4db-174">Converta o hash em uma cadeia de caracteres usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0e4db-174">Convert the hash to a string using UTF-8 encoding.</span></span>
* <span data-ttu-id="0e4db-175">Compare o valor da cadeia de caracteres do hash gerado com o valor fornecido na solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="0e4db-175">Compare the string value of the generated hash with the value provided in the HTTP request.</span></span>

# <a name="method-to-respond"></a>[<span data-ttu-id="0e4db-176">Método para responder</span><span class="sxs-lookup"><span data-stu-id="0e4db-176">Method to respond</span></span>](#tab/methodtorespond)
<span data-ttu-id="0e4db-177">**Criar um método para enviar uma resposta de sucesso ou falha**</span><span class="sxs-lookup"><span data-stu-id="0e4db-177">**Create a method to send a success or failure response**</span></span>

<span data-ttu-id="0e4db-178">As respostas de seus Webhooks de saída aparecem na mesma cadeia de resposta que a mensagem original.</span><span class="sxs-lookup"><span data-stu-id="0e4db-178">Responses from your Outgoing Webhooks appear in the same reply chain as the original message.</span></span> <span data-ttu-id="0e4db-179">Quando o usuário executa uma consulta, Microsoft Teams emite uma solicitação HTTP síncrona ao seu serviço e seu código obtém cinco segundos para responder à mensagem antes que a conexão seja encerrada e terminada.</span><span class="sxs-lookup"><span data-stu-id="0e4db-179">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service and your code gets five seconds to respond to the message before the connection times out and terminates.</span></span>

### <a name="example-response"></a><span data-ttu-id="0e4db-180">Resposta de exemplo</span><span class="sxs-lookup"><span data-stu-id="0e4db-180">Example response</span></span>

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```
---

> [!NOTE]
> * <span data-ttu-id="0e4db-181">Você pode enviar mensagens de texto e cartão adaptável como anexo com o Webhook de saída.</span><span class="sxs-lookup"><span data-stu-id="0e4db-181">You can send Adaptive Card, Hero card, and text messages as attachment with Outgoing Webhook.</span></span>
> * <span data-ttu-id="0e4db-182">Os cartões suportam formatação.</span><span class="sxs-lookup"><span data-stu-id="0e4db-182">Cards support formatting.</span></span> <span data-ttu-id="0e4db-183">Para obter mais informações, consulte [format cards with markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#format-cards-with-markdown).</span><span class="sxs-lookup"><span data-stu-id="0e4db-183">For more information, see [format cards with markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#format-cards-with-markdown).</span></span>

<span data-ttu-id="0e4db-184">Os códigos a seguir são exemplos de uma resposta do Cartão Adaptável:</span><span class="sxs-lookup"><span data-stu-id="0e4db-184">Following codes are examples of an Adaptive Card response:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="0e4db-185">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="0e4db-185">C#/.NET</span></span>](#tab/dotnet)

```csharp
string content = await this.Request.Content.ReadAsStringAsync();
Activity incomingActivity = JsonConvert.DeserializeObject<Activity>(content);

var Card = new AdaptiveCard(new AdaptiveSchemaVersion("1.4"))
{
    Body = new List<AdaptiveElement>()
    {
        new AdaptiveTextBlock(){Text= $"Request sent by: {incomingActivity.From.Name}"},
        new AdaptiveImage(){Url=new Uri("https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6")},
        new AdaptiveTextBlock(){Text="Sample image for Adaptive Card.."}
    }
};

var attachment = new Attachment()
{
    ContentType = AdaptiveCard.ContentType,
    Content = Card
};

var sampleResponseActivity = new Activity
{
    Attachments = new [] { attachment }
};

return sampleResponseActivity;
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="0e4db-186">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="0e4db-186">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
var receivedMsg = JSON.parse(payload);
var responseMsg = JSON.stringify({
    "type": "message",
    "attachments": [
        {
            "contentType": "application/vnd.microsoft.card.adaptive",
            "contentUrl": null,
            "content": {
                "type": "AdaptiveCard",
                "version": "1.4",
                "body": [
                    {
                        "type": "TextBlock",
                        "text": "Request sent by: " + receivedMsg.from.name
                    },
                    {
                        "type": "Image",
                        "url": "https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6"
                    },
                    {
                        "type": "TextBlock",
                        "text": "Sample image for Adaptive Card."
                    }
                ]
            },
            "name": null,
            "thumbnailUrl": null
        }
    ]
});
```

# <a name="json"></a>[<span data-ttu-id="0e4db-187">JSON</span><span class="sxs-lookup"><span data-stu-id="0e4db-187">JSON</span></span>](#tab/json)

```json
{
    "type": "message",
    "attachments": [
        {
            "contentType": "application/vnd.microsoft.card.adaptive",
            "content": {
                "type": "AdaptiveCard",
                "version": "1.4",
                "body": [
                    {
                        "type": "TextBlock",
                        "text": "Request sent by: Megan"
                    },
                    {
                        "type": "Image",
                        "url": "https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6"
                    },
                    {
                        "type": "TextBlock",
                        "text": "Sample image for Adaptive Card.."
                    }
                ]
            }
        }
    ]
}
```

* * *

## <a name="code-sample"></a><span data-ttu-id="0e4db-188">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="0e4db-188">Code sample</span></span>

|<span data-ttu-id="0e4db-189">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="0e4db-189">**Sample name**</span></span> | <span data-ttu-id="0e4db-190">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0e4db-190">**Description**</span></span> | <span data-ttu-id="0e4db-191">**.NET**</span><span class="sxs-lookup"><span data-stu-id="0e4db-191">**.NET**</span></span> | <span data-ttu-id="0e4db-192">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="0e4db-192">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="0e4db-193">Webhooks de saída</span><span class="sxs-lookup"><span data-stu-id="0e4db-193">Outgoing Webhooks</span></span> | <span data-ttu-id="0e4db-194">Exemplos para criar bots personalizados a serem usados em Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0e4db-194">Samples to create custom bots to be used in Microsoft Teams.</span></span>| [<span data-ttu-id="0e4db-195">View</span><span class="sxs-lookup"><span data-stu-id="0e4db-195">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [<span data-ttu-id="0e4db-196">View</span><span class="sxs-lookup"><span data-stu-id="0e4db-196">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

## <a name="see-also"></a><span data-ttu-id="0e4db-197">Também consulte</span><span class="sxs-lookup"><span data-stu-id="0e4db-197">See also</span></span>
* [<span data-ttu-id="0e4db-198">Criar um Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="0e4db-198">Create an Incoming Webhook</span></span>](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [<span data-ttu-id="0e4db-199">Criar um conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="0e4db-199">Create an Office 365 Connector</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [<span data-ttu-id="0e4db-200">Criar e enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="0e4db-200">Create and send messages</span></span>](~/webhooks-and-connectors/how-to/connectors-using.md)
