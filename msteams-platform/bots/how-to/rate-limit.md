---
title: Otimizar seu bot com limitação de fluxo no Teams
description: Limitação de taxas e práticas recomendadas no Microsoft Teams
ms.topic: conceptual
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 9a30d86a82a591c4a1125632fa7409780effb269
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2021
ms.locfileid: "51995852"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a><span data-ttu-id="652bc-104">Otimizar seu bot com limitação de fluxo no Teams</span><span class="sxs-lookup"><span data-stu-id="652bc-104">Optimize your bot with rate limiting in Teams</span></span>

<span data-ttu-id="652bc-105">Limitação de taxa é um método para limitar as mensagens a uma determinada frequência máxima.</span><span class="sxs-lookup"><span data-stu-id="652bc-105">Rate limiting is a method to limit messages to a certain maximum frequency.</span></span> <span data-ttu-id="652bc-106">Como um princípio geral, seu aplicativo deve limitar o número de mensagens que ele posta em um chat individual ou conversa de canal.</span><span class="sxs-lookup"><span data-stu-id="652bc-106">As a general principle, your application must limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="652bc-107">Isso garante uma experiência ideal e as mensagens não aparecem como spam para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="652bc-107">This ensures an optimal experience and messages do not appear as spam to your users.</span></span>

<span data-ttu-id="652bc-108">Para proteger o Microsoft Teams e seus usuários, as APIs de bot fornecem um limite de taxa para solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="652bc-108">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="652bc-109">Os aplicativos que passar por esse limite recebem um `HTTP 429 Too Many Requests` status de erro.</span><span class="sxs-lookup"><span data-stu-id="652bc-109">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="652bc-110">Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo o envio de mensagens, enumerações de canal e buscas de lista.</span><span class="sxs-lookup"><span data-stu-id="652bc-110">All requests are subject to the same rate limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="652bc-111">Como os valores exatos dos limites de taxa estão sujeitos a alterações, seu aplicativo deve implementar o comportamento de backoff apropriado quando a API retornar `HTTP 429 Too Many Requests` .</span><span class="sxs-lookup"><span data-stu-id="652bc-111">As the exact values of rate limits are subject to change, your application must implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handle-rate-limits"></a><span data-ttu-id="652bc-112">Manipular limites de taxa</span><span class="sxs-lookup"><span data-stu-id="652bc-112">Handle rate limits</span></span>

<span data-ttu-id="652bc-113">Ao emissão de uma operação SDK do Construtor de Bots, você pode manipular e `Microsoft.Rest.HttpOperationException` verificar o código de status.</span><span class="sxs-lookup"><span data-stu-id="652bc-113">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

<span data-ttu-id="652bc-114">O código a seguir mostra um exemplo de limites de taxa de manipulação:</span><span class="sxs-lookup"><span data-stu-id="652bc-114">The following code shows an example of handling rate limits:</span></span>

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

<span data-ttu-id="652bc-115">Depois de manipular os limites de taxa para bots, você pode lidar com respostas usando um `HTTP 429` backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="652bc-115">After you handle rate limits for bots, you can handle `HTTP 429` responses using an exponential backoff.</span></span>

## <a name="handle-http-429-responses"></a><span data-ttu-id="652bc-116">Manipular `HTTP 429` respostas</span><span class="sxs-lookup"><span data-stu-id="652bc-116">Handle `HTTP 429` responses</span></span>

<span data-ttu-id="652bc-117">Em geral, você deve tomar precauções simples para evitar receber `HTTP 429` respostas.</span><span class="sxs-lookup"><span data-stu-id="652bc-117">In general, you must take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="652bc-118">Por exemplo, evite a emissão de várias solicitações para a mesma conversa pessoal ou de canal.</span><span class="sxs-lookup"><span data-stu-id="652bc-118">For example, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="652bc-119">Em vez disso, crie um lote de solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="652bc-119">Instead, create a batch of the API requests.</span></span>

<span data-ttu-id="652bc-120">Usar um backoff exponencial com um tremeamento aleatório é a maneira recomendada de lidar com 429s.</span><span class="sxs-lookup"><span data-stu-id="652bc-120">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="652bc-121">Isso garante que várias solicitações não introduzam colisões em recuperações.</span><span class="sxs-lookup"><span data-stu-id="652bc-121">This ensures that multiple requests do not introduce collisions on retries.</span></span>

<span data-ttu-id="652bc-122">Depois de lidar `HTTP 429` com as respostas, você pode passar pelo exemplo para detectar exceções transitórias.</span><span class="sxs-lookup"><span data-stu-id="652bc-122">After you handle `HTTP 429` responses, you can go through the example for detecting transient exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="652bc-123">Além de retyring error code **429**, os códigos de erro **412**, **502** e **504** também devem ser retridados.</span><span class="sxs-lookup"><span data-stu-id="652bc-123">In addition to retyring error code **429**, error codes **412**, **502**, and **504** must also be retried.</span></span>

## <a name="detect-transient-exceptions-example"></a><span data-ttu-id="652bc-124">Exemplo de exceções transitórias</span><span class="sxs-lookup"><span data-stu-id="652bc-124">Detect transient exceptions example</span></span>

<span data-ttu-id="652bc-125">O código a seguir mostra um exemplo de uso de backoff exponencial usando o bloco de aplicativos de tratamento transitório de falhas:</span><span class="sxs-lookup"><span data-stu-id="652bc-125">The following code shows an example of using exponential backoff using the transient fault handling application block:</span></span>

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

<span data-ttu-id="652bc-126">Você pode executar o backoff e as recuperações usando o tratamento [transitório de falhas](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="652bc-126">You can perform backoff and retries using [transient fault handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="652bc-127">Para obter e instalar o pacote NuGet, consulte [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span><span class="sxs-lookup"><span data-stu-id="652bc-127">For guidelines on obtaining and installing the NuGet package, see [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span></span> <span data-ttu-id="652bc-128">Consulte também o [tratamento transitório de falhas](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="652bc-128">See also [transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

<span data-ttu-id="652bc-129">Depois de passar pelo exemplo para detectar exceções transitórias, vá pelo exemplo de backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="652bc-129">After you go through the example for detecting transient exceptions, go through the exponential backoff example.</span></span> <span data-ttu-id="652bc-130">Você pode usar o backoff exponencial em vez de repetir falhas.</span><span class="sxs-lookup"><span data-stu-id="652bc-130">You can use exponential backoff instead of retrying on failures.</span></span>

## <a name="backoff-example"></a><span data-ttu-id="652bc-131">Exemplo de backoff</span><span class="sxs-lookup"><span data-stu-id="652bc-131">Backoff example</span></span>

<span data-ttu-id="652bc-132">Além de detectar limites de taxa, você também pode executar um backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="652bc-132">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

<span data-ttu-id="652bc-133">O código a seguir mostra um exemplo de backoff exponencial:</span><span class="sxs-lookup"><span data-stu-id="652bc-133">The following code shows an example of exponential backoff:</span></span>

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

<span data-ttu-id="652bc-134">Você também pode executar uma execução `System.Action` de método com a política de nova tentativa descrita nesta seção.</span><span class="sxs-lookup"><span data-stu-id="652bc-134">You can also perform a `System.Action` method execution with the retry policy described in this section.</span></span> <span data-ttu-id="652bc-135">A biblioteca referenciada também permite especificar um intervalo fixo ou um mecanismo de backoff linear.</span><span class="sxs-lookup"><span data-stu-id="652bc-135">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="652bc-136">Armazene o valor e a estratégia em um arquivo de configuração para ajustar e ajustar valores em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="652bc-136">Store the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="652bc-137">Para obter mais informações, consulte [padrões de repetir](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="652bc-137">For more information, see [retry patterns](/azure/architecture/patterns/retry).</span></span>

<span data-ttu-id="652bc-138">Você também pode manipular o limite de taxa usando o bot por limite de thread.</span><span class="sxs-lookup"><span data-stu-id="652bc-138">You can also handle rate limit using the per bot per thread limit.</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="652bc-139">Por bot por limite de thread</span><span class="sxs-lookup"><span data-stu-id="652bc-139">Per bot per thread limit</span></span>

<span data-ttu-id="652bc-140">O limite por bot por thread controla o tráfego que um bot tem permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="652bc-140">The per bot per thread limit controls the traffic that a bot is allowed to generate in a single conversation.</span></span> <span data-ttu-id="652bc-141">Uma conversa é 1:1 entre bot e usuário, um chat em grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="652bc-141">A conversation is 1:1 between bot and user, a group chat, or a channel in a team.</span></span> <span data-ttu-id="652bc-142">Portanto, se o aplicativo enviar uma mensagem bot para cada usuário, o limite de thread não será limitado.</span><span class="sxs-lookup"><span data-stu-id="652bc-142">So, if the application sends one bot message to each user, the thread limit does not throttle.</span></span>

>[!NOTE]
> * <span data-ttu-id="652bc-143">O limite de thread de 3600 segundos e 1800 operações só se aplica se várias mensagens de bot são enviadas a um único usuário.</span><span class="sxs-lookup"><span data-stu-id="652bc-143">The thread limit of 3600 seconds and 1800 operations applies only if multiple bot messages are sent to a single user.</span></span> 
> * <span data-ttu-id="652bc-144">O limite global por aplicativo por locatário é de 30 solicitações por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="652bc-144">The global limit per app per tenant is 30 Requests Per Second (RPS).</span></span> <span data-ttu-id="652bc-145">Portanto, o número total de mensagens bot por segundo não deve cruzar o limite de thread.</span><span class="sxs-lookup"><span data-stu-id="652bc-145">Hence, the total number of bot messages per second must not cross the thread limit.</span></span>
> * <span data-ttu-id="652bc-146">A divisão de mensagens no nível de serviço resulta em RPS maior do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="652bc-146">Message splitting at the service level results in higher than expected RPS.</span></span> <span data-ttu-id="652bc-147">Se estiver preocupado com a abordagem dos limites, implemente a [estratégia de backoff](#backoff-example).</span><span class="sxs-lookup"><span data-stu-id="652bc-147">If you are concerned about approaching the limits, you must implement the [backoff strategy](#backoff-example).</span></span> <span data-ttu-id="652bc-148">Os valores fornecidos nesta seção são apenas para estimativa.</span><span class="sxs-lookup"><span data-stu-id="652bc-148">The values provided in this section are for estimation only.</span></span>

<span data-ttu-id="652bc-149">A tabela a seguir fornece os limites por bot por thread:</span><span class="sxs-lookup"><span data-stu-id="652bc-149">The following table provides the per bot per thread limits:</span></span>

| <span data-ttu-id="652bc-150">Cenário</span><span class="sxs-lookup"><span data-stu-id="652bc-150">Scenario</span></span> | <span data-ttu-id="652bc-151">Período de tempo em segundos</span><span class="sxs-lookup"><span data-stu-id="652bc-151">Time period in seconds</span></span> | <span data-ttu-id="652bc-152">Operações máximas permitidas</span><span class="sxs-lookup"><span data-stu-id="652bc-152">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="652bc-153">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-153">Send to conversation</span></span> | <span data-ttu-id="652bc-154">1</span><span class="sxs-lookup"><span data-stu-id="652bc-154">1</span></span> | <span data-ttu-id="652bc-155">7 </span><span class="sxs-lookup"><span data-stu-id="652bc-155">7</span></span> |
| <span data-ttu-id="652bc-156">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-156">Send to conversation</span></span> | <span data-ttu-id="652bc-157">2</span><span class="sxs-lookup"><span data-stu-id="652bc-157">2</span></span> | <span data-ttu-id="652bc-158">8 </span><span class="sxs-lookup"><span data-stu-id="652bc-158">8</span></span> |
| <span data-ttu-id="652bc-159">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-159">Send to conversation</span></span> | <span data-ttu-id="652bc-160">30</span><span class="sxs-lookup"><span data-stu-id="652bc-160">30</span></span> | <span data-ttu-id="652bc-161">60</span><span class="sxs-lookup"><span data-stu-id="652bc-161">60</span></span> |
| <span data-ttu-id="652bc-162">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-162">Send to conversation</span></span> | <span data-ttu-id="652bc-163">3600</span><span class="sxs-lookup"><span data-stu-id="652bc-163">3600</span></span> | <span data-ttu-id="652bc-164">1800</span><span class="sxs-lookup"><span data-stu-id="652bc-164">1800</span></span> |
| <span data-ttu-id="652bc-165">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-165">Create conversation</span></span> | <span data-ttu-id="652bc-166">1</span><span class="sxs-lookup"><span data-stu-id="652bc-166">1</span></span> | <span data-ttu-id="652bc-167">7 </span><span class="sxs-lookup"><span data-stu-id="652bc-167">7</span></span> |
| <span data-ttu-id="652bc-168">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-168">Create conversation</span></span> | <span data-ttu-id="652bc-169">2</span><span class="sxs-lookup"><span data-stu-id="652bc-169">2</span></span> | <span data-ttu-id="652bc-170">8 </span><span class="sxs-lookup"><span data-stu-id="652bc-170">8</span></span> |
| <span data-ttu-id="652bc-171">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-171">Create conversation</span></span> | <span data-ttu-id="652bc-172">30</span><span class="sxs-lookup"><span data-stu-id="652bc-172">30</span></span> | <span data-ttu-id="652bc-173">60</span><span class="sxs-lookup"><span data-stu-id="652bc-173">60</span></span> |
| <span data-ttu-id="652bc-174">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-174">Create conversation</span></span> | <span data-ttu-id="652bc-175">3600</span><span class="sxs-lookup"><span data-stu-id="652bc-175">3600</span></span> | <span data-ttu-id="652bc-176">1800</span><span class="sxs-lookup"><span data-stu-id="652bc-176">1800</span></span> |
| <span data-ttu-id="652bc-177">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-177">Get conversation members</span></span>| <span data-ttu-id="652bc-178">1</span><span class="sxs-lookup"><span data-stu-id="652bc-178">1</span></span> | <span data-ttu-id="652bc-179">14 </span><span class="sxs-lookup"><span data-stu-id="652bc-179">14</span></span> |
| <span data-ttu-id="652bc-180">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-180">Get conversation members</span></span>| <span data-ttu-id="652bc-181">2</span><span class="sxs-lookup"><span data-stu-id="652bc-181">2</span></span> | <span data-ttu-id="652bc-182">16 </span><span class="sxs-lookup"><span data-stu-id="652bc-182">16</span></span> |
| <span data-ttu-id="652bc-183">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-183">Get conversation members</span></span>| <span data-ttu-id="652bc-184">30</span><span class="sxs-lookup"><span data-stu-id="652bc-184">30</span></span> | <span data-ttu-id="652bc-185">120</span><span class="sxs-lookup"><span data-stu-id="652bc-185">120</span></span> |
| <span data-ttu-id="652bc-186">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-186">Get conversation members</span></span>| <span data-ttu-id="652bc-187">3600</span><span class="sxs-lookup"><span data-stu-id="652bc-187">3600</span></span> | <span data-ttu-id="652bc-188">3600</span><span class="sxs-lookup"><span data-stu-id="652bc-188">3600</span></span> |
| <span data-ttu-id="652bc-189">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="652bc-189">Get conversations</span></span> | <span data-ttu-id="652bc-190">1</span><span class="sxs-lookup"><span data-stu-id="652bc-190">1</span></span> | <span data-ttu-id="652bc-191">14 </span><span class="sxs-lookup"><span data-stu-id="652bc-191">14</span></span> |
| <span data-ttu-id="652bc-192">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="652bc-192">Get conversations</span></span> | <span data-ttu-id="652bc-193">2</span><span class="sxs-lookup"><span data-stu-id="652bc-193">2</span></span> | <span data-ttu-id="652bc-194">16 </span><span class="sxs-lookup"><span data-stu-id="652bc-194">16</span></span> |
| <span data-ttu-id="652bc-195">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="652bc-195">Get conversations</span></span> | <span data-ttu-id="652bc-196">30</span><span class="sxs-lookup"><span data-stu-id="652bc-196">30</span></span> | <span data-ttu-id="652bc-197">120</span><span class="sxs-lookup"><span data-stu-id="652bc-197">120</span></span> |
| <span data-ttu-id="652bc-198">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="652bc-198">Get conversations</span></span> | <span data-ttu-id="652bc-199">3600</span><span class="sxs-lookup"><span data-stu-id="652bc-199">3600</span></span> | <span data-ttu-id="652bc-200">3600</span><span class="sxs-lookup"><span data-stu-id="652bc-200">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="652bc-201">Versões anteriores `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` APIs estão sendo preterida.</span><span class="sxs-lookup"><span data-stu-id="652bc-201">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="652bc-202">Eles são sujeitos a cinco solicitações por minuto e retornam no máximo 10 mil membros por equipe.</span><span class="sxs-lookup"><span data-stu-id="652bc-202">They are throttled to five requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="652bc-203">Para atualizar o SDK da Estrutura de Bots e o código para usar os pontos de extremidade mais recentes da API paginada, consulte Alterações na API bot para membros de equipe [e chat.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="652bc-203">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="652bc-204">Você também pode manipular o limite de taxa usando o limite por thread para todos os bots.</span><span class="sxs-lookup"><span data-stu-id="652bc-204">You can also handle rate limit using the per thread limit for all bots.</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="652bc-205">Por limite de thread para todos os bots</span><span class="sxs-lookup"><span data-stu-id="652bc-205">Per thread limit for all bots</span></span>

<span data-ttu-id="652bc-206">O limite por thread para todos os bots controla o tráfego que todos os bots têm permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="652bc-206">The per thread limit for all bots controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="652bc-207">Uma conversa aqui é 1:1 entre bot e usuário, um chat em grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="652bc-207">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="652bc-208">A tabela a seguir fornece o limite por thread para todos os bots:</span><span class="sxs-lookup"><span data-stu-id="652bc-208">The following table provides the per thread limit for all bots:</span></span>

| <span data-ttu-id="652bc-209">Cenário</span><span class="sxs-lookup"><span data-stu-id="652bc-209">Scenario</span></span> | <span data-ttu-id="652bc-210">Período de tempo em segundos</span><span class="sxs-lookup"><span data-stu-id="652bc-210">Time period in seconds</span></span> | <span data-ttu-id="652bc-211">Operações máximas permitidas</span><span class="sxs-lookup"><span data-stu-id="652bc-211">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="652bc-212">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-212">Send to conversation</span></span> | <span data-ttu-id="652bc-213">1</span><span class="sxs-lookup"><span data-stu-id="652bc-213">1</span></span> | <span data-ttu-id="652bc-214">14 </span><span class="sxs-lookup"><span data-stu-id="652bc-214">14</span></span> |
| <span data-ttu-id="652bc-215">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-215">Send to conversation</span></span> | <span data-ttu-id="652bc-216">2</span><span class="sxs-lookup"><span data-stu-id="652bc-216">2</span></span> | <span data-ttu-id="652bc-217">16 </span><span class="sxs-lookup"><span data-stu-id="652bc-217">16</span></span> |
| <span data-ttu-id="652bc-218">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-218">Create conversation</span></span> | <span data-ttu-id="652bc-219">1</span><span class="sxs-lookup"><span data-stu-id="652bc-219">1</span></span> | <span data-ttu-id="652bc-220">14 </span><span class="sxs-lookup"><span data-stu-id="652bc-220">14</span></span> |
| <span data-ttu-id="652bc-221">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-221">Create conversation</span></span> | <span data-ttu-id="652bc-222">2</span><span class="sxs-lookup"><span data-stu-id="652bc-222">2</span></span> | <span data-ttu-id="652bc-223">16 </span><span class="sxs-lookup"><span data-stu-id="652bc-223">16</span></span> |
| <span data-ttu-id="652bc-224">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-224">Create conversation</span></span>| <span data-ttu-id="652bc-225">1</span><span class="sxs-lookup"><span data-stu-id="652bc-225">1</span></span> | <span data-ttu-id="652bc-226">14 </span><span class="sxs-lookup"><span data-stu-id="652bc-226">14</span></span> |
| <span data-ttu-id="652bc-227">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-227">Create conversation</span></span>| <span data-ttu-id="652bc-228">2</span><span class="sxs-lookup"><span data-stu-id="652bc-228">2</span></span> | <span data-ttu-id="652bc-229">16 </span><span class="sxs-lookup"><span data-stu-id="652bc-229">16</span></span> |
| <span data-ttu-id="652bc-230">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-230">Get conversation members</span></span>| <span data-ttu-id="652bc-231">1</span><span class="sxs-lookup"><span data-stu-id="652bc-231">1</span></span> | <span data-ttu-id="652bc-232">28</span><span class="sxs-lookup"><span data-stu-id="652bc-232">28</span></span> |
| <span data-ttu-id="652bc-233">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="652bc-233">Get conversation members</span></span>| <span data-ttu-id="652bc-234">2</span><span class="sxs-lookup"><span data-stu-id="652bc-234">2</span></span> | <span data-ttu-id="652bc-235">32</span><span class="sxs-lookup"><span data-stu-id="652bc-235">32</span></span> |
| <span data-ttu-id="652bc-236">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="652bc-236">Get conversations</span></span> | <span data-ttu-id="652bc-237">1</span><span class="sxs-lookup"><span data-stu-id="652bc-237">1</span></span> | <span data-ttu-id="652bc-238">28</span><span class="sxs-lookup"><span data-stu-id="652bc-238">28</span></span> |
| <span data-ttu-id="652bc-239">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="652bc-239">Get conversations</span></span> | <span data-ttu-id="652bc-240">2</span><span class="sxs-lookup"><span data-stu-id="652bc-240">2</span></span> | <span data-ttu-id="652bc-241">32</span><span class="sxs-lookup"><span data-stu-id="652bc-241">32</span></span> |

## <a name="next-step"></a><span data-ttu-id="652bc-242">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="652bc-242">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="652bc-243">Bots de chamadas e reuniões</span><span class="sxs-lookup"><span data-stu-id="652bc-243">Calls and meetings bots</span></span>](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

