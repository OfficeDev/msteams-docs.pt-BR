---
title: Otimizar seu bot com limitação de taxa no Teams
description: Limitação de taxas e práticas recomendadas no Microsoft Teams
ms.topic: conceptual
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 245c51fc736e5f888299535c3e50ec6232183623
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696994"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a><span data-ttu-id="3286a-104">Otimizar seu bot com limitação de taxa no Teams</span><span class="sxs-lookup"><span data-stu-id="3286a-104">Optimize your bot with rate limiting in Teams</span></span>

<span data-ttu-id="3286a-105">Limitação de taxa é um método para limitar as mensagens a uma determinada frequência máxima.</span><span class="sxs-lookup"><span data-stu-id="3286a-105">Rate limiting is a method to limit messages to a certain maximum frequency.</span></span> <span data-ttu-id="3286a-106">Como um princípio geral, seu aplicativo deve limitar o número de mensagens que ele posta em um chat individual ou conversa de canal.</span><span class="sxs-lookup"><span data-stu-id="3286a-106">As a general principle, your application must limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="3286a-107">Isso garante uma experiência ideal e as mensagens não aparecem como spam para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="3286a-107">This ensures an optimal experience and messages do not appear as spam to your users.</span></span>

<span data-ttu-id="3286a-108">Para proteger o Microsoft Teams e seus usuários, as APIs de bot fornecem um limite de taxa para solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="3286a-108">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="3286a-109">Os aplicativos que passar por esse limite recebem um `HTTP 429 Too Many Requests` status de erro.</span><span class="sxs-lookup"><span data-stu-id="3286a-109">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="3286a-110">Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo o envio de mensagens, enumerações de canal e buscas de lista.</span><span class="sxs-lookup"><span data-stu-id="3286a-110">All requests are subject to the same rate limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="3286a-111">Como os valores exatos dos limites de taxa estão sujeitos a alterações, seu aplicativo deve implementar o comportamento de backoff apropriado quando a API retornar `HTTP 429 Too Many Requests` .</span><span class="sxs-lookup"><span data-stu-id="3286a-111">As the exact values of rate limits are subject to change, your application must implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handle-rate-limits"></a><span data-ttu-id="3286a-112">Manipular limites de taxa</span><span class="sxs-lookup"><span data-stu-id="3286a-112">Handle rate limits</span></span>

<span data-ttu-id="3286a-113">Ao emissão de uma operação SDK do Construtor de Bots, você pode manipular e `Microsoft.Rest.HttpOperationException` verificar o código de status.</span><span class="sxs-lookup"><span data-stu-id="3286a-113">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

<span data-ttu-id="3286a-114">O código a seguir mostra um exemplo de limites de taxa de manipulação:</span><span class="sxs-lookup"><span data-stu-id="3286a-114">The following code shows an example of handling rate limits:</span></span>

```csharp
try
{
    // Perform Bot Framework operation
    // for example, await connector.Conversations.UpdateActivityAsync(reply);
}
catch (HttpOperationException ex)
{
    if (ex.Response != null && (uint)ex.Response.StatusCode ==  429)
    {
        //Perform retry of the above operation/Action method
    }
}
```

<span data-ttu-id="3286a-115">Depois de manipular os limites de taxa para bots, você pode lidar com respostas usando um `HTTP 429` backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="3286a-115">After you handle rate limits for bots, you can handle `HTTP 429` responses using an exponential backoff.</span></span>

## <a name="handle-http-429-responses"></a><span data-ttu-id="3286a-116">Manipular `HTTP 429` respostas</span><span class="sxs-lookup"><span data-stu-id="3286a-116">Handle `HTTP 429` responses</span></span>

<span data-ttu-id="3286a-117">Em geral, você deve tomar precauções simples para evitar receber `HTTP 429` respostas.</span><span class="sxs-lookup"><span data-stu-id="3286a-117">In general, you must take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="3286a-118">Por exemplo, evite a emissão de várias solicitações para a mesma conversa pessoal ou de canal.</span><span class="sxs-lookup"><span data-stu-id="3286a-118">For example, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="3286a-119">Em vez disso, crie um lote de solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="3286a-119">Instead, create a batch of the API requests.</span></span>

<span data-ttu-id="3286a-120">Usar um backoff exponencial com um tremeamento aleatório é a maneira recomendada de lidar com 429s.</span><span class="sxs-lookup"><span data-stu-id="3286a-120">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="3286a-121">Isso garante que várias solicitações não introduzam colisões em recuperações.</span><span class="sxs-lookup"><span data-stu-id="3286a-121">This ensures that multiple requests do not introduce collisions on retries.</span></span>

<span data-ttu-id="3286a-122">Depois de lidar `HTTP 429` com as respostas, você pode passar pelo exemplo para detectar exceções transitórias.</span><span class="sxs-lookup"><span data-stu-id="3286a-122">After you handle `HTTP 429` responses, you can go through the example for detecting transient exceptions.</span></span>

## <a name="detect-transient-exceptions-example"></a><span data-ttu-id="3286a-123">Exemplo de exceções transitórias</span><span class="sxs-lookup"><span data-stu-id="3286a-123">Detect transient exceptions example</span></span>

<span data-ttu-id="3286a-124">O código a seguir mostra um exemplo de uso de backoff exponencial usando o bloco de aplicativos de tratamento transitório de falhas:</span><span class="sxs-lookup"><span data-stu-id="3286a-124">The following code shows an example of using exponential backoff using the transient fault handling application block:</span></span>

```csharp
public class BotSdkTransientExceptionDetectionStrategy : ITransientErrorDetectionStrategy
    {
        // List of error codes to retry on
        List<int> transientErrorStatusCodes = new List<int>() { 429 };

        public bool IsTransient(Exception ex)
        {
            if (ex.Message.Contains("429"))
                return true;

            var httpOperationException = ex as HttpOperationException;
            if (httpOperationException != null)
            {
                return httpOperationException.Response != null &&
                        transientErrorStatusCodes.Contains((int)httpOperationException.Response.StatusCode);
            }

            return false;
        }
    }
```

<span data-ttu-id="3286a-125">Você pode executar o backoff e as recuperações usando o tratamento [transitório de falhas](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="3286a-125">You can perform backoff and retries using [transient fault handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="3286a-126">Para obter e instalar o pacote NuGet, consulte [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span><span class="sxs-lookup"><span data-stu-id="3286a-126">For guidelines on obtaining and installing the NuGet package, see [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span></span> <span data-ttu-id="3286a-127">Consulte também o [tratamento transitório de falhas](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="3286a-127">See also [transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

<span data-ttu-id="3286a-128">Depois de passar pelo exemplo para detectar exceções transitórias, vá pelo exemplo de backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="3286a-128">After you go through the example for detecting transient exceptions, go through the exponential backoff example.</span></span> <span data-ttu-id="3286a-129">Você pode usar o backoff exponencial em vez de repetir falhas.</span><span class="sxs-lookup"><span data-stu-id="3286a-129">You can use exponential backoff instead of retrying on failures.</span></span>

## <a name="backoff-example"></a><span data-ttu-id="3286a-130">Exemplo de backoff</span><span class="sxs-lookup"><span data-stu-id="3286a-130">Backoff example</span></span>

<span data-ttu-id="3286a-131">Além de detectar limites de taxa, você também pode executar um backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="3286a-131">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

<span data-ttu-id="3286a-132">O código a seguir mostra um exemplo de backoff exponencial:</span><span class="sxs-lookup"><span data-stu-id="3286a-132">The following code shows an example of exponential backoff:</span></span>

```csharp
/**
* The first parameter specifies the number of retries before failing the operation.
* The second parameter specifies the minimum and maximum backoff time respectively.
* The last parameter is used to add a randomized  +/- 20% delta to avoid numerous clients retrying simultaneously.
*/
var exponentialBackoffRetryStrategy = new ExponentialBackoff(3, TimeSpan.FromSeconds(2),
                        TimeSpan.FromSeconds(20), TimeSpan.FromSeconds(1));


// Define the Retry Policy
var retryPolicy = new RetryPolicy(new BotSdkTransientExceptionDetectionStrategy(), exponentialBackoffRetryStrategy);

//Execute any bot sdk action
await retryPolicy.ExecuteAsync(() => connector.Conversations.ReplyToActivityAsync( (Activity)reply) ).ConfigureAwait(false);
```

<span data-ttu-id="3286a-133">Você também pode executar uma execução `System.Action` de método com a política de nova tentativa descrita nesta seção.</span><span class="sxs-lookup"><span data-stu-id="3286a-133">You can also perform a `System.Action` method execution with the retry policy described in this section.</span></span> <span data-ttu-id="3286a-134">A biblioteca referenciada também permite especificar um intervalo fixo ou um mecanismo de backoff linear.</span><span class="sxs-lookup"><span data-stu-id="3286a-134">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="3286a-135">Armazene o valor e a estratégia em um arquivo de configuração para ajustar e ajustar valores em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3286a-135">Store the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="3286a-136">Para obter mais informações, consulte [padrões de repetir](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="3286a-136">For more information, see [retry patterns](/azure/architecture/patterns/retry).</span></span>

<span data-ttu-id="3286a-137">Você também pode manipular o limite de taxa usando o bot por limite de thread.</span><span class="sxs-lookup"><span data-stu-id="3286a-137">You can also handle rate limit using the per bot per thread limit.</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="3286a-138">Por bot por limite de thread</span><span class="sxs-lookup"><span data-stu-id="3286a-138">Per bot per thread limit</span></span>

>[!NOTE]
> <span data-ttu-id="3286a-139">A divisão de mensagens no nível de serviço resulta em solicitações mais altas do que as esperadas por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="3286a-139">Message splitting at the service level results in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="3286a-140">Se estiver preocupado com a abordagem dos limites, implemente a [estratégia de backoff](#backoff-example).</span><span class="sxs-lookup"><span data-stu-id="3286a-140">If you are concerned about approaching the limits, you must implement the [backoff strategy](#backoff-example).</span></span> <span data-ttu-id="3286a-141">Os valores fornecidos nesta seção são apenas para estimativa.</span><span class="sxs-lookup"><span data-stu-id="3286a-141">The values provided in this section are for estimation only.</span></span>

<span data-ttu-id="3286a-142">O limite por bot por thread controla o tráfego que um bot tem permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="3286a-142">The per bot per thread limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="3286a-143">Uma conversa aqui é 1:1 entre bot e usuário, um chat em grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="3286a-143">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="3286a-144">A tabela a seguir fornece os limites por bot por thread:</span><span class="sxs-lookup"><span data-stu-id="3286a-144">The following table provides the per bot per thread limits:</span></span>

| <span data-ttu-id="3286a-145">Cenário</span><span class="sxs-lookup"><span data-stu-id="3286a-145">Scenario</span></span> | <span data-ttu-id="3286a-146">Período de tempo em segundos</span><span class="sxs-lookup"><span data-stu-id="3286a-146">Time period in seconds</span></span> | <span data-ttu-id="3286a-147">Operações máximas permitidas</span><span class="sxs-lookup"><span data-stu-id="3286a-147">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3286a-148">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-148">Send to conversation</span></span> | <span data-ttu-id="3286a-149">1</span><span class="sxs-lookup"><span data-stu-id="3286a-149">1</span></span> | <span data-ttu-id="3286a-150">7 </span><span class="sxs-lookup"><span data-stu-id="3286a-150">7</span></span> |
| <span data-ttu-id="3286a-151">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-151">Send to conversation</span></span> | <span data-ttu-id="3286a-152">2</span><span class="sxs-lookup"><span data-stu-id="3286a-152">2</span></span> | <span data-ttu-id="3286a-153">8 </span><span class="sxs-lookup"><span data-stu-id="3286a-153">8</span></span> |
| <span data-ttu-id="3286a-154">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-154">Send to conversation</span></span> | <span data-ttu-id="3286a-155">30</span><span class="sxs-lookup"><span data-stu-id="3286a-155">30</span></span> | <span data-ttu-id="3286a-156">60</span><span class="sxs-lookup"><span data-stu-id="3286a-156">60</span></span> |
| <span data-ttu-id="3286a-157">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-157">Send to conversation</span></span> | <span data-ttu-id="3286a-158">3600</span><span class="sxs-lookup"><span data-stu-id="3286a-158">3600</span></span> | <span data-ttu-id="3286a-159">1800</span><span class="sxs-lookup"><span data-stu-id="3286a-159">1800</span></span> |
| <span data-ttu-id="3286a-160">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-160">Create conversation</span></span> | <span data-ttu-id="3286a-161">1</span><span class="sxs-lookup"><span data-stu-id="3286a-161">1</span></span> | <span data-ttu-id="3286a-162">7 </span><span class="sxs-lookup"><span data-stu-id="3286a-162">7</span></span> |
| <span data-ttu-id="3286a-163">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-163">Create conversation</span></span> | <span data-ttu-id="3286a-164">2</span><span class="sxs-lookup"><span data-stu-id="3286a-164">2</span></span> | <span data-ttu-id="3286a-165">8 </span><span class="sxs-lookup"><span data-stu-id="3286a-165">8</span></span> |
| <span data-ttu-id="3286a-166">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-166">Create conversation</span></span> | <span data-ttu-id="3286a-167">30</span><span class="sxs-lookup"><span data-stu-id="3286a-167">30</span></span> | <span data-ttu-id="3286a-168">60</span><span class="sxs-lookup"><span data-stu-id="3286a-168">60</span></span> |
| <span data-ttu-id="3286a-169">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-169">Create conversation</span></span> | <span data-ttu-id="3286a-170">3600</span><span class="sxs-lookup"><span data-stu-id="3286a-170">3600</span></span> | <span data-ttu-id="3286a-171">1800</span><span class="sxs-lookup"><span data-stu-id="3286a-171">1800</span></span> |
| <span data-ttu-id="3286a-172">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-172">Get conversation members</span></span>| <span data-ttu-id="3286a-173">1</span><span class="sxs-lookup"><span data-stu-id="3286a-173">1</span></span> | <span data-ttu-id="3286a-174">14 </span><span class="sxs-lookup"><span data-stu-id="3286a-174">14</span></span> |
| <span data-ttu-id="3286a-175">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-175">Get conversation members</span></span>| <span data-ttu-id="3286a-176">2</span><span class="sxs-lookup"><span data-stu-id="3286a-176">2</span></span> | <span data-ttu-id="3286a-177">16 </span><span class="sxs-lookup"><span data-stu-id="3286a-177">16</span></span> |
| <span data-ttu-id="3286a-178">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-178">Get conversation members</span></span>| <span data-ttu-id="3286a-179">30</span><span class="sxs-lookup"><span data-stu-id="3286a-179">30</span></span> | <span data-ttu-id="3286a-180">120</span><span class="sxs-lookup"><span data-stu-id="3286a-180">120</span></span> |
| <span data-ttu-id="3286a-181">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-181">Get conversation members</span></span>| <span data-ttu-id="3286a-182">3600</span><span class="sxs-lookup"><span data-stu-id="3286a-182">3600</span></span> | <span data-ttu-id="3286a-183">3600</span><span class="sxs-lookup"><span data-stu-id="3286a-183">3600</span></span> |
| <span data-ttu-id="3286a-184">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="3286a-184">Get conversations</span></span> | <span data-ttu-id="3286a-185">1</span><span class="sxs-lookup"><span data-stu-id="3286a-185">1</span></span> | <span data-ttu-id="3286a-186">14 </span><span class="sxs-lookup"><span data-stu-id="3286a-186">14</span></span> |
| <span data-ttu-id="3286a-187">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="3286a-187">Get conversations</span></span> | <span data-ttu-id="3286a-188">2</span><span class="sxs-lookup"><span data-stu-id="3286a-188">2</span></span> | <span data-ttu-id="3286a-189">16 </span><span class="sxs-lookup"><span data-stu-id="3286a-189">16</span></span> |
| <span data-ttu-id="3286a-190">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="3286a-190">Get conversations</span></span> | <span data-ttu-id="3286a-191">30</span><span class="sxs-lookup"><span data-stu-id="3286a-191">30</span></span> | <span data-ttu-id="3286a-192">120</span><span class="sxs-lookup"><span data-stu-id="3286a-192">120</span></span> |
| <span data-ttu-id="3286a-193">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="3286a-193">Get conversations</span></span> | <span data-ttu-id="3286a-194">3600</span><span class="sxs-lookup"><span data-stu-id="3286a-194">3600</span></span> | <span data-ttu-id="3286a-195">3600</span><span class="sxs-lookup"><span data-stu-id="3286a-195">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="3286a-196">Versões anteriores `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` APIs estão sendo preterida.</span><span class="sxs-lookup"><span data-stu-id="3286a-196">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="3286a-197">Eles são sujeitos a cinco solicitações por minuto e retornam no máximo 10 mil membros por equipe.</span><span class="sxs-lookup"><span data-stu-id="3286a-197">They are throttled to five requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="3286a-198">Para atualizar o SDK da Estrutura de Bots e o código para usar os pontos de extremidade mais recentes da API paginada, consulte Alterações na API bot para membros de equipe [e chat.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="3286a-198">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="3286a-199">Você também pode manipular o limite de taxa usando o limite por thread para todos os bots.</span><span class="sxs-lookup"><span data-stu-id="3286a-199">You can also handle rate limit using the per thread limit for all bots.</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="3286a-200">Por limite de thread para todos os bots</span><span class="sxs-lookup"><span data-stu-id="3286a-200">Per thread limit for all bots</span></span>

<span data-ttu-id="3286a-201">O limite por thread para todos os bots controla o tráfego que todos os bots têm permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="3286a-201">The per thread limit for all bots controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="3286a-202">Uma conversa aqui é 1:1 entre bot e usuário, um chat em grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="3286a-202">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="3286a-203">A tabela a seguir fornece o limite por thread para todos os bots:</span><span class="sxs-lookup"><span data-stu-id="3286a-203">The following table provides the per thread limit for all bots:</span></span>

| <span data-ttu-id="3286a-204">Cenário</span><span class="sxs-lookup"><span data-stu-id="3286a-204">Scenario</span></span> | <span data-ttu-id="3286a-205">Período de tempo em segundos</span><span class="sxs-lookup"><span data-stu-id="3286a-205">Time period in seconds</span></span> | <span data-ttu-id="3286a-206">Operações máximas permitidas</span><span class="sxs-lookup"><span data-stu-id="3286a-206">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3286a-207">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-207">Send to conversation</span></span> | <span data-ttu-id="3286a-208">1</span><span class="sxs-lookup"><span data-stu-id="3286a-208">1</span></span> | <span data-ttu-id="3286a-209">14 </span><span class="sxs-lookup"><span data-stu-id="3286a-209">14</span></span> |
| <span data-ttu-id="3286a-210">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-210">Send to conversation</span></span> | <span data-ttu-id="3286a-211">2</span><span class="sxs-lookup"><span data-stu-id="3286a-211">2</span></span> | <span data-ttu-id="3286a-212">16 </span><span class="sxs-lookup"><span data-stu-id="3286a-212">16</span></span> |
| <span data-ttu-id="3286a-213">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-213">Create conversation</span></span> | <span data-ttu-id="3286a-214">1</span><span class="sxs-lookup"><span data-stu-id="3286a-214">1</span></span> | <span data-ttu-id="3286a-215">14 </span><span class="sxs-lookup"><span data-stu-id="3286a-215">14</span></span> |
| <span data-ttu-id="3286a-216">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-216">Create conversation</span></span> | <span data-ttu-id="3286a-217">2</span><span class="sxs-lookup"><span data-stu-id="3286a-217">2</span></span> | <span data-ttu-id="3286a-218">16 </span><span class="sxs-lookup"><span data-stu-id="3286a-218">16</span></span> |
| <span data-ttu-id="3286a-219">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-219">Create conversation</span></span>| <span data-ttu-id="3286a-220">1</span><span class="sxs-lookup"><span data-stu-id="3286a-220">1</span></span> | <span data-ttu-id="3286a-221">14 </span><span class="sxs-lookup"><span data-stu-id="3286a-221">14</span></span> |
| <span data-ttu-id="3286a-222">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-222">Create conversation</span></span>| <span data-ttu-id="3286a-223">2</span><span class="sxs-lookup"><span data-stu-id="3286a-223">2</span></span> | <span data-ttu-id="3286a-224">16 </span><span class="sxs-lookup"><span data-stu-id="3286a-224">16</span></span> |
| <span data-ttu-id="3286a-225">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-225">Get conversation members</span></span>| <span data-ttu-id="3286a-226">1</span><span class="sxs-lookup"><span data-stu-id="3286a-226">1</span></span> | <span data-ttu-id="3286a-227">28</span><span class="sxs-lookup"><span data-stu-id="3286a-227">28</span></span> |
| <span data-ttu-id="3286a-228">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="3286a-228">Get conversation members</span></span>| <span data-ttu-id="3286a-229">2</span><span class="sxs-lookup"><span data-stu-id="3286a-229">2</span></span> | <span data-ttu-id="3286a-230">32</span><span class="sxs-lookup"><span data-stu-id="3286a-230">32</span></span> |
| <span data-ttu-id="3286a-231">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="3286a-231">Get conversations</span></span> | <span data-ttu-id="3286a-232">1</span><span class="sxs-lookup"><span data-stu-id="3286a-232">1</span></span> | <span data-ttu-id="3286a-233">28</span><span class="sxs-lookup"><span data-stu-id="3286a-233">28</span></span> |
| <span data-ttu-id="3286a-234">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="3286a-234">Get conversations</span></span> | <span data-ttu-id="3286a-235">2</span><span class="sxs-lookup"><span data-stu-id="3286a-235">2</span></span> | <span data-ttu-id="3286a-236">32</span><span class="sxs-lookup"><span data-stu-id="3286a-236">32</span></span> |

## <a name="next-step"></a><span data-ttu-id="3286a-237">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="3286a-237">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3286a-238">Bots de chamadas e reuniões</span><span class="sxs-lookup"><span data-stu-id="3286a-238">Calls and meetings bots</span></span>](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

