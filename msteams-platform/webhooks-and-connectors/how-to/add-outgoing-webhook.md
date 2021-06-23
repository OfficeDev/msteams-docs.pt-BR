---
title: Adicionar bots personalizados para Microsoft Teams com webhooks de saída
description: descreve como adicionar um webhook de saída
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: guias do teams webhook de saída mensagem ativas verificar webhook
ms.openlocfilehash: 2fac6f42e27a4c8cb3d079ea281d458a4dfe41ed
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069180"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a><span data-ttu-id="4c963-104">Adicionar bots personalizados para Teams com webhooks de saída</span><span class="sxs-lookup"><span data-stu-id="4c963-104">Add custom bots to Teams with outgoing webhooks</span></span>

## <a name="outgoing-webhooks-in-teams"></a><span data-ttu-id="4c963-105">Webhooks de saída em Teams</span><span class="sxs-lookup"><span data-stu-id="4c963-105">Outgoing webhooks in Teams</span></span>

<span data-ttu-id="4c963-106">Webhooks são uma maneira proeminente de Teams se integrar com aplicativos externos.</span><span class="sxs-lookup"><span data-stu-id="4c963-106">Webhooks are an eminent way for Teams to integrate with external apps.</span></span> <span data-ttu-id="4c963-107">Um webhook é essencialmente uma solicitação POST enviada para uma URL de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="4c963-107">A webhook is essentially a POST request sent to a callback URL.</span></span> <span data-ttu-id="4c963-108">Webhooks de saída permitem que os usuários enviem mensagens para seu serviço Web sem passar pelo processo completo de criação de bots por meio do [Microsoft Bot Framework](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="4c963-108">Outgoing webhooks allow users to send messages to your web service without going through the full process of creating bots via the [Microsoft Bot Framework](https://dev.botframework.com/).</span></span>

<span data-ttu-id="4c963-109">O webhook de saída envia dados de Teams para qualquer serviço escolhido capaz de aceitar uma carga JSON.</span><span class="sxs-lookup"><span data-stu-id="4c963-109">Outgoing webhook sends data from Teams to any chosen service capable of accepting a JSON payload.</span></span> <span data-ttu-id="4c963-110">Depois de adicionar os webhooks de saída a uma equipe, ele age como um bot e procura mensagens em canais usando **\@ menção**.</span><span class="sxs-lookup"><span data-stu-id="4c963-110">After adding the outgoing webhooks to a team, it acts as a bot and looks for messages in channels using **\@mention**.</span></span> <span data-ttu-id="4c963-111">Ele envia notificações para serviços Web externos e responde com mensagens ricas, que incluem cartões e imagens.</span><span class="sxs-lookup"><span data-stu-id="4c963-111">It sends notifications to external web services and responds with rich messages, which include cards and images.</span></span>

## <a name="outgoing-webhook-key-features"></a><span data-ttu-id="4c963-112">Recursos de chave de webhook de saída</span><span class="sxs-lookup"><span data-stu-id="4c963-112">Outgoing webhook key features</span></span>

| <span data-ttu-id="4c963-113">Recurso</span><span class="sxs-lookup"><span data-stu-id="4c963-113">Feature</span></span> | <span data-ttu-id="4c963-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c963-114">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="4c963-115">Configuração com escopo</span><span class="sxs-lookup"><span data-stu-id="4c963-115">Scoped configuration</span></span>| <span data-ttu-id="4c963-116">Os webhooks têm escopo no nível da equipe.</span><span class="sxs-lookup"><span data-stu-id="4c963-116">Webhooks are scoped at the team level.</span></span> <span data-ttu-id="4c963-117">Você deve passar pelo processo de instalação de cada equipe onde deseja adicionar seu webhook de saída.</span><span class="sxs-lookup"><span data-stu-id="4c963-117">You must go through the setup process for each team where you want to add your outgoing webhook.</span></span> |
| <span data-ttu-id="4c963-118">Mensagens reativas</span><span class="sxs-lookup"><span data-stu-id="4c963-118">Reactive messaging</span></span>| <span data-ttu-id="4c963-119">Os usuários devem usar @mention webhook para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="4c963-119">Users must use @mention for the webhook to receive messages.</span></span> <span data-ttu-id="4c963-120">Atualmente, os usuários só podem enviar um webhook de saída em canais públicos e não no escopo pessoal ou privado.</span><span class="sxs-lookup"><span data-stu-id="4c963-120">Currently, users can only message an outgoing webhook in public channels and not within the personal or private scope.</span></span> |
|<span data-ttu-id="4c963-121">Troca de mensagens HTTP padrão</span><span class="sxs-lookup"><span data-stu-id="4c963-121">Standard HTTP message exchange</span></span>|<span data-ttu-id="4c963-122">As respostas aparecem na mesma cadeia que a mensagem de solicitação original e podem incluir qualquer conteúdo de mensagem de estrutura de bot, por exemplo, texto rico, imagens, cartões e emojis.</span><span class="sxs-lookup"><span data-stu-id="4c963-122">Responses appear in the same chain as the original request message and can include any bot framework message content, for example, rich text, images, cards, and emojis.</span></span> <span data-ttu-id="4c963-123">Embora os webhooks de saída possam usar cartões, eles não podem usar nenhuma ação de cartão, exceto `openURL` por .</span><span class="sxs-lookup"><span data-stu-id="4c963-123">Although outgoing webhooks can use cards, they cannot use any card actions except for `openURL`.</span></span>|
| <span data-ttu-id="4c963-124">Teams Suporte ao método API</span><span class="sxs-lookup"><span data-stu-id="4c963-124">Teams API method support</span></span>|<span data-ttu-id="4c963-125">O webhook de saída envia um HTTP POST para um serviço Web e processa uma resposta de volta.</span><span class="sxs-lookup"><span data-stu-id="4c963-125">Outgoing webhook sends an HTTP POST to a web service and process a response back.</span></span> <span data-ttu-id="4c963-126">Eles não podem acessar outras APIs, como recuperar a lista ou a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="4c963-126">They cannot access any other APIs like retrieve the roster or list of channels in a team.</span></span>|

## <a name="creating-actionable-messages"></a><span data-ttu-id="4c963-127">Criar mensagens acionáveis</span><span class="sxs-lookup"><span data-stu-id="4c963-127">Creating actionable messages</span></span>

<span data-ttu-id="4c963-128">Os cartões de conector incluem três botões visíveis no cartão.</span><span class="sxs-lookup"><span data-stu-id="4c963-128">The connector cards include three visible buttons on the card.</span></span> <span data-ttu-id="4c963-129">Cada botão é definido na `potentialAction` propriedade da mensagem usando `ActionCard` ações.</span><span class="sxs-lookup"><span data-stu-id="4c963-129">Each button is defined in the `potentialAction` property of the message by using `ActionCard` actions.</span></span> <span data-ttu-id="4c963-130">Cada `ActionCard` um contém um tipo de entrada; um campo de texto, um selador de datas ou uma lista de várias opções.</span><span class="sxs-lookup"><span data-stu-id="4c963-130">Each `ActionCard` contains an input type; a text field, a date picker, or a multi-choice list.</span></span> <span data-ttu-id="4c963-131">Cada `ActionCard` ação tem uma ação associada, por exemplo, `HttpPOST` .</span><span class="sxs-lookup"><span data-stu-id="4c963-131">Each `ActionCard` action has an associated action, for example, `HttpPOST`.</span></span>

<span data-ttu-id="4c963-132">Os cartões do conector oferecem suporte a três tipos de ações:</span><span class="sxs-lookup"><span data-stu-id="4c963-132">Connector cards support three types of actions:</span></span>

| <span data-ttu-id="4c963-133">Ação</span><span class="sxs-lookup"><span data-stu-id="4c963-133">Action</span></span> | <span data-ttu-id="4c963-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c963-134">Description</span></span> |
| ------- | ----------- |
| `ActionCard` |<span data-ttu-id="4c963-135">Apresenta um ou mais tipos de entrada e ações associadas.</span><span class="sxs-lookup"><span data-stu-id="4c963-135">Presents one or more input types and associated actions.</span></span>|
| `HttpPOST` | <span data-ttu-id="4c963-136">Envia uma solicitação POST a uma URL.</span><span class="sxs-lookup"><span data-stu-id="4c963-136">Sends a POST request to a URL.</span></span> |
| `OpenUri` |  <span data-ttu-id="4c963-137">Abre um URI em um navegador ou aplicativo separado, opcionalmente direciona URIs diferentes com base em sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="4c963-137">Opens a URI in a separate browser or app, optionally targets different URIs based on operating systems.</span></span>|

<span data-ttu-id="4c963-138">A ação `ActionCard` oferece suporte a três tipos de entrada:</span><span class="sxs-lookup"><span data-stu-id="4c963-138">The `ActionCard` action supports three input types:</span></span>

| <span data-ttu-id="4c963-139">Tipo de entrada</span><span class="sxs-lookup"><span data-stu-id="4c963-139">Input type</span></span> | <span data-ttu-id="4c963-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c963-140">Description</span></span> |
| ------- | ----------- |
| `TextInput` | <span data-ttu-id="4c963-141">Um campo de texto de linha única ou multilinha com um limite de comprimento opcional.</span><span class="sxs-lookup"><span data-stu-id="4c963-141">A single-line or multiline text field with an optional length limit.</span></span> |
| `DateInput` | <span data-ttu-id="4c963-142">Um seletor de datas com um seletor de hora opcional.</span><span class="sxs-lookup"><span data-stu-id="4c963-142">A date selector with an optional time selector.</span></span> |
| `MultichoiceInput` | <span data-ttu-id="4c963-143">Uma lista especificada de opções, oferecendo uma única seleção ou várias seleções.</span><span class="sxs-lookup"><span data-stu-id="4c963-143">A specified list of choices, offering either a single selection or multiple selections.</span></span>|

<span data-ttu-id="4c963-144">`MultichoiceInput` suporta uma `style` propriedade que controla a exibição de uma lista totalmente expandida.</span><span class="sxs-lookup"><span data-stu-id="4c963-144">`MultichoiceInput` supports a `style` property that controls the display of a fully expanded list.</span></span> <span data-ttu-id="4c963-145">O valor padrão de `style` depende do `isMultiSelect` valor.</span><span class="sxs-lookup"><span data-stu-id="4c963-145">The default value of `style` depends on the `isMultiSelect` value.</span></span>

| <span data-ttu-id="4c963-146">`isMultiSelect` value</span><span class="sxs-lookup"><span data-stu-id="4c963-146">`isMultiSelect` value</span></span>  | <span data-ttu-id="4c963-147">`style` valor padrão</span><span class="sxs-lookup"><span data-stu-id="4c963-147">`style` default value</span></span>  |
| --- | --- |
| <span data-ttu-id="4c963-148">`false` ou não especificado </span><span class="sxs-lookup"><span data-stu-id="4c963-148">`false` or not specified</span></span> | <span data-ttu-id="4c963-149">O estilo padrão é `compact`</span><span class="sxs-lookup"><span data-stu-id="4c963-149">The default style is `compact`</span></span>|
| `true` | <span data-ttu-id="4c963-150">O estilo padrão é `expanded`</span><span class="sxs-lookup"><span data-stu-id="4c963-150">The default style is `expanded`</span></span> |

> [!NOTE]
> * <span data-ttu-id="4c963-151">Insira ambos e , se você quiser que a lista `"isMultiSelect": true` `"style": true` multiseleccionada seja exibida em um estilo compacto.</span><span class="sxs-lookup"><span data-stu-id="4c963-151">Enter both `"isMultiSelect": true` and `"style": true`, if you want the multi-select list to be displayed in a compact style.</span></span>
> * <span data-ttu-id="4c963-152">Selecionar para a propriedade no Teams é o mesmo que `compact` selecionar para a propriedade no Microsoft `style` `normal` `style` Outlook.</span><span class="sxs-lookup"><span data-stu-id="4c963-152">Selecting `compact` for the `style` property in Teams is the same as selecting `normal` for the `style` property in Microsoft Outlook.</span></span>
> * <span data-ttu-id="4c963-153">Os Webhooks suportam apenas Office 365 de retorno de mensagens e cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="4c963-153">Webhooks support only Office 365 message back cards and adaptive cards.</span></span>

<span data-ttu-id="4c963-154">Para obter todos os outros detalhes sobre ações de cartão de conector, consulte **[Actions](/outlook/actionable-messages/card-reference#actions)** na referência do cartão de mensagem a actionable.</span><span class="sxs-lookup"><span data-stu-id="4c963-154">For all other details about connector card actions, see **[Actions](/outlook/actionable-messages/card-reference#actions)** in the actionable message card reference.</span></span>

## <a name="adding-outgoing-webhooks-to-your-app"></a><span data-ttu-id="4c963-155">Adicionar webhooks de saída ao seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4c963-155">Adding outgoing webhooks to your app</span></span>

<span data-ttu-id="4c963-156">**Cenário**: Notificações de status de alteração por push em um servidor de banco de dados Teams canal para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c963-156">**Scenario**: Push change status notifications on a Teams channel database server to your app.</span></span>  
<span data-ttu-id="4c963-157">**Exemplo:** você tem um aplicativo de linha de negócios que rastreia todas as operações CRU Teams D feitas em registros de funcionários por usuários de RH de canal em uma Office 365 de terceiros.</span><span class="sxs-lookup"><span data-stu-id="4c963-157">**Example**: You have a line-of-business app that tracks all CRUD operations made to employee records by Teams channel HR users across an Office 365 tenancy.</span></span>

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a><span data-ttu-id="4c963-158">1. Crie uma URL no servidor do aplicativo para aceitar e processar uma solicitação POST com uma carga JSON</span><span class="sxs-lookup"><span data-stu-id="4c963-158">1. Create a URL on your app's server to accept and process a POST request with a JSON payload</span></span>

<span data-ttu-id="4c963-159">Seu serviço recebe mensagens em um esquema de mensagens de serviço de bot padrão do Azure.</span><span class="sxs-lookup"><span data-stu-id="4c963-159">Your service receives messages in a standard Azure bot service messaging schema.</span></span> <span data-ttu-id="4c963-160">O conector de estrutura de bot é um serviço RESTful que capacita seu serviço a processar o intercâmbio de mensagens formatadas JSON por meio de protocolos HTTPS, conforme documentado na API de Serviço de Bot do [Azure.](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)</span><span class="sxs-lookup"><span data-stu-id="4c963-160">The bot framework connector is a RESTful service that empowers your service to process the interchange of JSON formatted messages via HTTPS protocols as documented in the [Azure Bot Service API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).</span></span> <span data-ttu-id="4c963-161">Como alternativa, você pode seguir o [Microsoft Bot Framework SDK] para processar e analisar mensagens.</span><span class="sxs-lookup"><span data-stu-id="4c963-161">Alternatively, you can follow the [Microsoft Bot Framework SDK] to process and parse messages.</span></span> <span data-ttu-id="4c963-162">Consulte também [Sobre o serviço bot do Azure.](/azure/bot-service/bot-service-overview-introduction)</span><span class="sxs-lookup"><span data-stu-id="4c963-162">See also [About Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).</span></span>


<span data-ttu-id="4c963-163">Os webhooks de saída têm escopo para o `team` nível e são visíveis para todos os membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="4c963-163">Outgoing webhooks are scoped to the `team` level and are visible to all the team members.</span></span> <span data-ttu-id="4c963-164">Assim como um bot, os usuários precisam **\@ mencionar** o nome do webhook de saída para invocá-lo no canal.</span><span class="sxs-lookup"><span data-stu-id="4c963-164">Just like a bot, users need to **\@mention** the name of the outgoing webhook to invoke it in the channel.</span></span>

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a><span data-ttu-id="4c963-165">2. Crie um método para verificar o token HMAC de webhook de saída</span><span class="sxs-lookup"><span data-stu-id="4c963-165">2. Create a method to verify the outgoing webhook HMAC token</span></span>

#### <a name="hmac-signature-for-testing-with-code-example"></a><span data-ttu-id="4c963-166">Assinatura HMAC para teste com exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4c963-166">HMAC signature for testing with code example</span></span>

<span data-ttu-id="4c963-167">Usando exemplo de mensagem de entrada e id: "contoso" de SigningKeyDictionary de {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.</span><span class="sxs-lookup"><span data-stu-id="4c963-167">Using example of inbound message and id: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.</span></span>

<span data-ttu-id="4c963-168">Use o valor "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" na autorização do header de solicitação.</span><span class="sxs-lookup"><span data-stu-id="4c963-168">Use the value "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in the authorization of request header.</span></span>

<span data-ttu-id="4c963-169">Para garantir que seu serviço receba chamadas somente de clientes Teams reais, o Teams fornece um código HMAC no `hmac` cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c963-169">To ensure that your service is receiving calls only from actual Teams clients, Teams provides an HMAC code in the HTTP `hmac` header.</span></span> <span data-ttu-id="4c963-170">Sempre incluiu o código em seu protocolo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="4c963-170">Always included the code in your authentication protocol.</span></span>

<span data-ttu-id="4c963-171">Seu código deve sempre validar a assinatura HMAC incluída na solicitação:</span><span class="sxs-lookup"><span data-stu-id="4c963-171">Your code must always validate the HMAC signature included in the request:</span></span>

* <span data-ttu-id="4c963-172">Gere o token HMAC do corpo da solicitação da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4c963-172">Generate the HMAC token from the request body of the message.</span></span> <span data-ttu-id="4c963-173">Há bibliotecas padrão para fazer isso na maioria das plataformas (consulte [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js ou [consulte Teams Webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C \# ).</span><span class="sxs-lookup"><span data-stu-id="4c963-173">There are standard libraries to do this on most platforms (see [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js or see [Teams Webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C\#).</span></span> <span data-ttu-id="4c963-174">Microsoft Teams usa criptografia HMAC SHA256 padrão.</span><span class="sxs-lookup"><span data-stu-id="4c963-174">Microsoft Teams uses standard SHA256 HMAC cryptography.</span></span> <span data-ttu-id="4c963-175">Você precisa converter o corpo em uma matriz de byte em UTF8.</span><span class="sxs-lookup"><span data-stu-id="4c963-175">You need to convert the body to a byte array in UTF8.</span></span>
* <span data-ttu-id="4c963-176">Compute o hash da matriz de byte do token de segurança fornecido pelo **Teams** quando você registrou o webhook de saída no cliente Teams].</span><span class="sxs-lookup"><span data-stu-id="4c963-176">Compute the hash from the byte array of the security token **provided by Teams** when you registered the outgoing webhook in the Teams client].</span></span> <span data-ttu-id="4c963-177">Consulte [Criar um webhook de saída.](#create-an-outgoing-webhook)</span><span class="sxs-lookup"><span data-stu-id="4c963-177">See [Create an outgoing webhook](#create-an-outgoing-webhook).</span></span>
* <span data-ttu-id="4c963-178">Converta o hash em uma cadeia de caracteres usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4c963-178">Convert the hash to a string using UTF-8 encoding.</span></span>
* <span data-ttu-id="4c963-179">Compare o valor da cadeia de caracteres do hash gerado com o valor fornecido na solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c963-179">Compare the string value of the generated hash with the value provided in the HTTP request.</span></span>

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a><span data-ttu-id="4c963-180">3. Crie um método para enviar uma resposta de sucesso ou falha</span><span class="sxs-lookup"><span data-stu-id="4c963-180">3. Create a method to send a success or failure response</span></span>

<span data-ttu-id="4c963-181">As respostas de seus webhooks de saída aparecem na mesma cadeia de resposta que a mensagem original.</span><span class="sxs-lookup"><span data-stu-id="4c963-181">Responses from your outgoing webhooks appear in the same reply chain as the original message.</span></span> <span data-ttu-id="4c963-182">Quando o usuário executa uma consulta, Microsoft Teams emite uma solicitação HTTP síncrona ao seu serviço e seu código obtém cinco segundos para responder à mensagem antes que a conexão seja encerrada e terminada.</span><span class="sxs-lookup"><span data-stu-id="4c963-182">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service and your code gets five seconds to respond to the message before the connection times out and terminates.</span></span>

### <a name="example-response"></a><span data-ttu-id="4c963-183">Resposta de exemplo</span><span class="sxs-lookup"><span data-stu-id="4c963-183">Example response</span></span>

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

> [!NOTE]
> * <span data-ttu-id="4c963-184">Você pode enviar mensagens de texto e cartão adaptável como anexo com webhook de saída.</span><span class="sxs-lookup"><span data-stu-id="4c963-184">You can send Adaptive Card, Hero card, and text messages as attachment with outgoing webhook.</span></span>
> * <span data-ttu-id="4c963-185">Os cartões suportam formatação.</span><span class="sxs-lookup"><span data-stu-id="4c963-185">Cards support formatting.</span></span> <span data-ttu-id="4c963-186">Para obter mais informações, consulte [format cards with markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#formatting-cards-with-markdown).</span><span class="sxs-lookup"><span data-stu-id="4c963-186">For more information, see [format cards with markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#formatting-cards-with-markdown).</span></span>

<span data-ttu-id="4c963-187">Os códigos a seguir são exemplos de uma resposta do Cartão Adaptável:</span><span class="sxs-lookup"><span data-stu-id="4c963-187">Following codes are examples of an Adaptive Card response:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="4c963-188">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="4c963-188">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="4c963-189">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="4c963-189">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="4c963-190">JSON</span><span class="sxs-lookup"><span data-stu-id="4c963-190">JSON</span></span>](#tab/json)

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

## <a name="create-an-outgoing-webhook"></a><span data-ttu-id="4c963-191">Criar um webhook de saída</span><span class="sxs-lookup"><span data-stu-id="4c963-191">Create an outgoing webhook</span></span>

1. <span data-ttu-id="4c963-192">Selecione a equipe apropriada e escolha **Gerenciar equipe** no menu suspenso (&#8226;&#8226;&#8226;) suspenso.</span><span class="sxs-lookup"><span data-stu-id="4c963-192">Select the appropriate team and choose **Manage team** from the (&#8226;&#8226;&#8226;) drop-down menu.</span></span>
1. <span data-ttu-id="4c963-193">Escolha a **guia Aplicativos** na barra de navegação.</span><span class="sxs-lookup"><span data-stu-id="4c963-193">Choose the **Apps** tab from the navigation bar.</span></span>
1. <span data-ttu-id="4c963-194">No canto inferior direito da janela, selecione **Criar um webhook de saída.**</span><span class="sxs-lookup"><span data-stu-id="4c963-194">From the window's lower right corner select **Create an outgoing webhook**.</span></span>
1. <span data-ttu-id="4c963-195">Na janela pop-up resultante, conclua os campos necessários:</span><span class="sxs-lookup"><span data-stu-id="4c963-195">In the resulting popup window complete the required fields:</span></span>

>* <span data-ttu-id="4c963-196">**Nome**: o título de webhook e @mention toque</span><span class="sxs-lookup"><span data-stu-id="4c963-196">**Name**: The webhook title and @mention tap</span></span>
>* <span data-ttu-id="4c963-197">**URL de retorno** de chamada : o ponto de extremidade HTTPS que aceita cargas JSON e recebe solicitações POST de Teams</span><span class="sxs-lookup"><span data-stu-id="4c963-197">**Callback URL**: The HTTPS endpoint that accepts JSON payloads and receives POST requests from Teams</span></span>
>* <span data-ttu-id="4c963-198">**Descrição**: uma cadeia de caracteres detalhada que aparece no cartão de perfil e no painel de aplicativos no nível da equipe</span><span class="sxs-lookup"><span data-stu-id="4c963-198">**Description**: A detailed string that appear in the profile card and the team-level App dashboard</span></span>
>* <span data-ttu-id="4c963-199">**Imagem do** perfil : um ícone de aplicativo opcional para seu webhook</span><span class="sxs-lookup"><span data-stu-id="4c963-199">**Profile Picture**: An optional app icon for your webhook</span></span>
>* <span data-ttu-id="4c963-200">Selecione o **botão Criar** no canto inferior direito da janela pop-up e o webhook de saída é adicionado aos canais da equipe atual.</span><span class="sxs-lookup"><span data-stu-id="4c963-200">Select the **Create** button from the lower right corner of the pop-up window and the outgoing webhook are added to the current team's channels.</span></span>
>* <span data-ttu-id="4c963-201">A próxima janela de diálogo exibe um token de segurança [HMAC (Código](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) de Autenticação de Mensagem) baseado em hash que é usado para autenticar chamadas entre Teams e o serviço externo designado.</span><span class="sxs-lookup"><span data-stu-id="4c963-201">The next dialog window displays an [Hash-based Message Authentication Code (HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) security token that is used to authenticate calls between Teams and the designated outside service.</span></span>
>* <span data-ttu-id="4c963-202">O webhook de saída está disponível para os usuários da equipe, somente se a URL for válida e os tokens de autenticação de servidor e cliente são iguais, por exemplo, um aperto de mão HMAC.</span><span class="sxs-lookup"><span data-stu-id="4c963-202">The outgoing webhook is available to the team's users, only if the URL is valid and the server and client authentication tokens are equal for example, an HMAC handshake.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4c963-203">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4c963-203">Code sample</span></span>
|<span data-ttu-id="4c963-204">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="4c963-204">**Sample name**</span></span> | <span data-ttu-id="4c963-205">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4c963-205">**Description**</span></span> | <span data-ttu-id="4c963-206">**.NET**</span><span class="sxs-lookup"><span data-stu-id="4c963-206">**.NET**</span></span> | <span data-ttu-id="4c963-207">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="4c963-207">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="4c963-208">Webhooks de saída</span><span class="sxs-lookup"><span data-stu-id="4c963-208">Outgoing webhooks</span></span> | <span data-ttu-id="4c963-209">Exemplos para criar **Bots Personalizados** a serem usados em Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4c963-209">Samples to create **Custom Bots** to be used in Microsoft Teams.</span></span>| [<span data-ttu-id="4c963-210">View</span><span class="sxs-lookup"><span data-stu-id="4c963-210">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [<span data-ttu-id="4c963-211">View</span><span class="sxs-lookup"><span data-stu-id="4c963-211">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

