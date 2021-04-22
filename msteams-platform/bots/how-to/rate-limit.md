---
title: Otimizar seu bot com limitação de fluxo no Teams
description: Limitação de taxas e práticas recomendadas no Microsoft Teams
ms.topic: conceptual
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 690d09e4a3b611c024f32d3776ca73e42d63ee7f
ms.sourcegitcommit: 35bc2a31b92f3f7c6524373108f095a870d9ad09
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51922500"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a><span data-ttu-id="ab190-104">Otimizar seu bot com limitação de fluxo no Teams</span><span class="sxs-lookup"><span data-stu-id="ab190-104">Optimize your bot with rate limiting in Teams</span></span>

<span data-ttu-id="ab190-105">Limitação de taxa é um método para limitar as mensagens a uma determinada frequência máxima.</span><span class="sxs-lookup"><span data-stu-id="ab190-105">Rate limiting is a method to limit messages to a certain maximum frequency.</span></span> <span data-ttu-id="ab190-106">Como um princípio geral, seu aplicativo deve limitar o número de mensagens que ele posta em um chat individual ou conversa de canal.</span><span class="sxs-lookup"><span data-stu-id="ab190-106">As a general principle, your application must limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="ab190-107">Isso garante uma experiência ideal e as mensagens não aparecem como spam para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="ab190-107">This ensures an optimal experience and messages do not appear as spam to your users.</span></span>

<span data-ttu-id="ab190-108">Para proteger o Microsoft Teams e seus usuários, as APIs de bot fornecem um limite de taxa para solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="ab190-108">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="ab190-109">Os aplicativos que passar por esse limite recebem um `HTTP 429 Too Many Requests` status de erro.</span><span class="sxs-lookup"><span data-stu-id="ab190-109">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="ab190-110">Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo o envio de mensagens, enumerações de canal e buscas de lista.</span><span class="sxs-lookup"><span data-stu-id="ab190-110">All requests are subject to the same rate limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="ab190-111">Como os valores exatos dos limites de taxa estão sujeitos a alterações, seu aplicativo deve implementar o comportamento de backoff apropriado quando a API retornar `HTTP 429 Too Many Requests` .</span><span class="sxs-lookup"><span data-stu-id="ab190-111">As the exact values of rate limits are subject to change, your application must implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handle-rate-limits"></a><span data-ttu-id="ab190-112">Manipular limites de taxa</span><span class="sxs-lookup"><span data-stu-id="ab190-112">Handle rate limits</span></span>

<span data-ttu-id="ab190-113">Ao emissão de uma operação SDK do Construtor de Bots, você pode manipular e `Microsoft.Rest.HttpOperationException` verificar o código de status.</span><span class="sxs-lookup"><span data-stu-id="ab190-113">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

<span data-ttu-id="ab190-114">O código a seguir mostra um exemplo de limites de taxa de manipulação:</span><span class="sxs-lookup"><span data-stu-id="ab190-114">The following code shows an example of handling rate limits:</span></span>

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

<span data-ttu-id="ab190-115">Depois de manipular os limites de taxa para bots, você pode lidar com respostas usando um `HTTP 429` backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="ab190-115">After you handle rate limits for bots, you can handle `HTTP 429` responses using an exponential backoff.</span></span>

## <a name="handle-http-429-responses"></a><span data-ttu-id="ab190-116">Manipular `HTTP 429` respostas</span><span class="sxs-lookup"><span data-stu-id="ab190-116">Handle `HTTP 429` responses</span></span>

<span data-ttu-id="ab190-117">Em geral, você deve tomar precauções simples para evitar receber `HTTP 429` respostas.</span><span class="sxs-lookup"><span data-stu-id="ab190-117">In general, you must take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="ab190-118">Por exemplo, evite a emissão de várias solicitações para a mesma conversa pessoal ou de canal.</span><span class="sxs-lookup"><span data-stu-id="ab190-118">For example, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="ab190-119">Em vez disso, crie um lote de solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="ab190-119">Instead, create a batch of the API requests.</span></span>

<span data-ttu-id="ab190-120">Usar um backoff exponencial com um tremeamento aleatório é a maneira recomendada de lidar com 429s.</span><span class="sxs-lookup"><span data-stu-id="ab190-120">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="ab190-121">Isso garante que várias solicitações não introduzam colisões em recuperações.</span><span class="sxs-lookup"><span data-stu-id="ab190-121">This ensures that multiple requests do not introduce collisions on retries.</span></span>

<span data-ttu-id="ab190-122">Depois de lidar `HTTP 429` com as respostas, você pode passar pelo exemplo para detectar exceções transitórias.</span><span class="sxs-lookup"><span data-stu-id="ab190-122">After you handle `HTTP 429` responses, you can go through the example for detecting transient exceptions.</span></span>

## <a name="detect-transient-exceptions-example"></a><span data-ttu-id="ab190-123">Exemplo de exceções transitórias</span><span class="sxs-lookup"><span data-stu-id="ab190-123">Detect transient exceptions example</span></span>

<span data-ttu-id="ab190-124">O código a seguir mostra um exemplo de uso de backoff exponencial usando o bloco de aplicativos de tratamento transitório de falhas:</span><span class="sxs-lookup"><span data-stu-id="ab190-124">The following code shows an example of using exponential backoff using the transient fault handling application block:</span></span>

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

<span data-ttu-id="ab190-125">Você pode executar o backoff e as recuperações usando o tratamento [transitório de falhas](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="ab190-125">You can perform backoff and retries using [transient fault handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="ab190-126">Para obter e instalar o pacote NuGet, consulte [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span><span class="sxs-lookup"><span data-stu-id="ab190-126">For guidelines on obtaining and installing the NuGet package, see [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span></span> <span data-ttu-id="ab190-127">Consulte também o [tratamento transitório de falhas](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="ab190-127">See also [transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

<span data-ttu-id="ab190-128">Depois de passar pelo exemplo para detectar exceções transitórias, vá pelo exemplo de backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="ab190-128">After you go through the example for detecting transient exceptions, go through the exponential backoff example.</span></span> <span data-ttu-id="ab190-129">Você pode usar o backoff exponencial em vez de repetir falhas.</span><span class="sxs-lookup"><span data-stu-id="ab190-129">You can use exponential backoff instead of retrying on failures.</span></span>

## <a name="backoff-example"></a><span data-ttu-id="ab190-130">Exemplo de backoff</span><span class="sxs-lookup"><span data-stu-id="ab190-130">Backoff example</span></span>

<span data-ttu-id="ab190-131">Além de detectar limites de taxa, você também pode executar um backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="ab190-131">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

<span data-ttu-id="ab190-132">O código a seguir mostra um exemplo de backoff exponencial:</span><span class="sxs-lookup"><span data-stu-id="ab190-132">The following code shows an example of exponential backoff:</span></span>

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

<span data-ttu-id="ab190-133">Você também pode executar uma execução `System.Action` de método com a política de nova tentativa descrita nesta seção.</span><span class="sxs-lookup"><span data-stu-id="ab190-133">You can also perform a `System.Action` method execution with the retry policy described in this section.</span></span> <span data-ttu-id="ab190-134">A biblioteca referenciada também permite especificar um intervalo fixo ou um mecanismo de backoff linear.</span><span class="sxs-lookup"><span data-stu-id="ab190-134">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="ab190-135">Armazene o valor e a estratégia em um arquivo de configuração para ajustar e ajustar valores em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ab190-135">Store the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="ab190-136">Para obter mais informações, consulte [padrões de repetir](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="ab190-136">For more information, see [retry patterns](/azure/architecture/patterns/retry).</span></span>

<span data-ttu-id="ab190-137">Você também pode manipular o limite de taxa usando o bot por limite de thread.</span><span class="sxs-lookup"><span data-stu-id="ab190-137">You can also handle rate limit using the per bot per thread limit.</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="ab190-138">Por bot por limite de thread</span><span class="sxs-lookup"><span data-stu-id="ab190-138">Per bot per thread limit</span></span>

<span data-ttu-id="ab190-139">O limite por bot por thread controla o tráfego que um bot tem permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="ab190-139">The per bot per thread limit controls the traffic that a bot is allowed to generate in a single conversation.</span></span> <span data-ttu-id="ab190-140">Uma conversa é 1:1 entre bot e usuário, um chat em grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="ab190-140">A conversation is 1:1 between bot and user, a group chat, or a channel in a team.</span></span> <span data-ttu-id="ab190-141">Portanto, se o aplicativo enviar uma mensagem bot para cada usuário, o limite de thread não será limitado.</span><span class="sxs-lookup"><span data-stu-id="ab190-141">So, if the application sends one bot message to each user, the thread limit does not throttle.</span></span>

>[!NOTE]
> * <span data-ttu-id="ab190-142">O limite de thread de 3600 segundos e 1800 operações só se aplica se várias mensagens de bot são enviadas a um único usuário.</span><span class="sxs-lookup"><span data-stu-id="ab190-142">The thread limit of 3600 seconds and 1800 operations applies only if multiple bot messages are sent to a single user.</span></span> 
> * <span data-ttu-id="ab190-143">O limite global por aplicativo por locatário é de 30 solicitações por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="ab190-143">The global limit per app per tenant is 30 Requests Per Second (RPS).</span></span> <span data-ttu-id="ab190-144">Portanto, o número total de mensagens bot por segundo não deve cruzar o limite de thread.</span><span class="sxs-lookup"><span data-stu-id="ab190-144">Hence, the total number of bot messages per second must not cross the thread limit.</span></span>
> * <span data-ttu-id="ab190-145">A divisão de mensagens no nível de serviço resulta em RPS maior do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="ab190-145">Message splitting at the service level results in higher than expected RPS.</span></span> <span data-ttu-id="ab190-146">Se estiver preocupado com a abordagem dos limites, implemente a [estratégia de backoff](#backoff-example).</span><span class="sxs-lookup"><span data-stu-id="ab190-146">If you are concerned about approaching the limits, you must implement the [backoff strategy](#backoff-example).</span></span> <span data-ttu-id="ab190-147">Os valores fornecidos nesta seção são apenas para estimativa.</span><span class="sxs-lookup"><span data-stu-id="ab190-147">The values provided in this section are for estimation only.</span></span>

<span data-ttu-id="ab190-148">A tabela a seguir fornece os limites por bot por thread:</span><span class="sxs-lookup"><span data-stu-id="ab190-148">The following table provides the per bot per thread limits:</span></span>

| <span data-ttu-id="ab190-149">Cenário</span><span class="sxs-lookup"><span data-stu-id="ab190-149">Scenario</span></span> | <span data-ttu-id="ab190-150">Período de tempo em segundos</span><span class="sxs-lookup"><span data-stu-id="ab190-150">Time period in seconds</span></span> | <span data-ttu-id="ab190-151">Operações máximas permitidas</span><span class="sxs-lookup"><span data-stu-id="ab190-151">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="ab190-152">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-152">Send to conversation</span></span> | <span data-ttu-id="ab190-153">1</span><span class="sxs-lookup"><span data-stu-id="ab190-153">1</span></span> | <span data-ttu-id="ab190-154">7 </span><span class="sxs-lookup"><span data-stu-id="ab190-154">7</span></span> |
| <span data-ttu-id="ab190-155">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-155">Send to conversation</span></span> | <span data-ttu-id="ab190-156">2</span><span class="sxs-lookup"><span data-stu-id="ab190-156">2</span></span> | <span data-ttu-id="ab190-157">8 </span><span class="sxs-lookup"><span data-stu-id="ab190-157">8</span></span> |
| <span data-ttu-id="ab190-158">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-158">Send to conversation</span></span> | <span data-ttu-id="ab190-159">30</span><span class="sxs-lookup"><span data-stu-id="ab190-159">30</span></span> | <span data-ttu-id="ab190-160">60</span><span class="sxs-lookup"><span data-stu-id="ab190-160">60</span></span> |
| <span data-ttu-id="ab190-161">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-161">Send to conversation</span></span> | <span data-ttu-id="ab190-162">3600</span><span class="sxs-lookup"><span data-stu-id="ab190-162">3600</span></span> | <span data-ttu-id="ab190-163">1800</span><span class="sxs-lookup"><span data-stu-id="ab190-163">1800</span></span> |
| <span data-ttu-id="ab190-164">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-164">Create conversation</span></span> | <span data-ttu-id="ab190-165">1</span><span class="sxs-lookup"><span data-stu-id="ab190-165">1</span></span> | <span data-ttu-id="ab190-166">7 </span><span class="sxs-lookup"><span data-stu-id="ab190-166">7</span></span> |
| <span data-ttu-id="ab190-167">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-167">Create conversation</span></span> | <span data-ttu-id="ab190-168">2</span><span class="sxs-lookup"><span data-stu-id="ab190-168">2</span></span> | <span data-ttu-id="ab190-169">8 </span><span class="sxs-lookup"><span data-stu-id="ab190-169">8</span></span> |
| <span data-ttu-id="ab190-170">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-170">Create conversation</span></span> | <span data-ttu-id="ab190-171">30</span><span class="sxs-lookup"><span data-stu-id="ab190-171">30</span></span> | <span data-ttu-id="ab190-172">60</span><span class="sxs-lookup"><span data-stu-id="ab190-172">60</span></span> |
| <span data-ttu-id="ab190-173">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-173">Create conversation</span></span> | <span data-ttu-id="ab190-174">3600</span><span class="sxs-lookup"><span data-stu-id="ab190-174">3600</span></span> | <span data-ttu-id="ab190-175">1800</span><span class="sxs-lookup"><span data-stu-id="ab190-175">1800</span></span> |
| <span data-ttu-id="ab190-176">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-176">Get conversation members</span></span>| <span data-ttu-id="ab190-177">1</span><span class="sxs-lookup"><span data-stu-id="ab190-177">1</span></span> | <span data-ttu-id="ab190-178">14 </span><span class="sxs-lookup"><span data-stu-id="ab190-178">14</span></span> |
| <span data-ttu-id="ab190-179">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-179">Get conversation members</span></span>| <span data-ttu-id="ab190-180">2</span><span class="sxs-lookup"><span data-stu-id="ab190-180">2</span></span> | <span data-ttu-id="ab190-181">16 </span><span class="sxs-lookup"><span data-stu-id="ab190-181">16</span></span> |
| <span data-ttu-id="ab190-182">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-182">Get conversation members</span></span>| <span data-ttu-id="ab190-183">30</span><span class="sxs-lookup"><span data-stu-id="ab190-183">30</span></span> | <span data-ttu-id="ab190-184">120</span><span class="sxs-lookup"><span data-stu-id="ab190-184">120</span></span> |
| <span data-ttu-id="ab190-185">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-185">Get conversation members</span></span>| <span data-ttu-id="ab190-186">3600</span><span class="sxs-lookup"><span data-stu-id="ab190-186">3600</span></span> | <span data-ttu-id="ab190-187">3600</span><span class="sxs-lookup"><span data-stu-id="ab190-187">3600</span></span> |
| <span data-ttu-id="ab190-188">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="ab190-188">Get conversations</span></span> | <span data-ttu-id="ab190-189">1</span><span class="sxs-lookup"><span data-stu-id="ab190-189">1</span></span> | <span data-ttu-id="ab190-190">14 </span><span class="sxs-lookup"><span data-stu-id="ab190-190">14</span></span> |
| <span data-ttu-id="ab190-191">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="ab190-191">Get conversations</span></span> | <span data-ttu-id="ab190-192">2</span><span class="sxs-lookup"><span data-stu-id="ab190-192">2</span></span> | <span data-ttu-id="ab190-193">16 </span><span class="sxs-lookup"><span data-stu-id="ab190-193">16</span></span> |
| <span data-ttu-id="ab190-194">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="ab190-194">Get conversations</span></span> | <span data-ttu-id="ab190-195">30</span><span class="sxs-lookup"><span data-stu-id="ab190-195">30</span></span> | <span data-ttu-id="ab190-196">120</span><span class="sxs-lookup"><span data-stu-id="ab190-196">120</span></span> |
| <span data-ttu-id="ab190-197">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="ab190-197">Get conversations</span></span> | <span data-ttu-id="ab190-198">3600</span><span class="sxs-lookup"><span data-stu-id="ab190-198">3600</span></span> | <span data-ttu-id="ab190-199">3600</span><span class="sxs-lookup"><span data-stu-id="ab190-199">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="ab190-200">Versões anteriores `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` APIs estão sendo preterida.</span><span class="sxs-lookup"><span data-stu-id="ab190-200">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="ab190-201">Eles são sujeitos a cinco solicitações por minuto e retornam no máximo 10 mil membros por equipe.</span><span class="sxs-lookup"><span data-stu-id="ab190-201">They are throttled to five requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="ab190-202">Para atualizar o SDK da Estrutura de Bots e o código para usar os pontos de extremidade mais recentes da API paginada, consulte Alterações na API bot para membros de equipe [e chat.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="ab190-202">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="ab190-203">Você também pode manipular o limite de taxa usando o limite por thread para todos os bots.</span><span class="sxs-lookup"><span data-stu-id="ab190-203">You can also handle rate limit using the per thread limit for all bots.</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="ab190-204">Por limite de thread para todos os bots</span><span class="sxs-lookup"><span data-stu-id="ab190-204">Per thread limit for all bots</span></span>

<span data-ttu-id="ab190-205">O limite por thread para todos os bots controla o tráfego que todos os bots têm permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="ab190-205">The per thread limit for all bots controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="ab190-206">Uma conversa aqui é 1:1 entre bot e usuário, um chat em grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="ab190-206">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="ab190-207">A tabela a seguir fornece o limite por thread para todos os bots:</span><span class="sxs-lookup"><span data-stu-id="ab190-207">The following table provides the per thread limit for all bots:</span></span>

| <span data-ttu-id="ab190-208">Cenário</span><span class="sxs-lookup"><span data-stu-id="ab190-208">Scenario</span></span> | <span data-ttu-id="ab190-209">Período de tempo em segundos</span><span class="sxs-lookup"><span data-stu-id="ab190-209">Time period in seconds</span></span> | <span data-ttu-id="ab190-210">Operações máximas permitidas</span><span class="sxs-lookup"><span data-stu-id="ab190-210">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="ab190-211">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-211">Send to conversation</span></span> | <span data-ttu-id="ab190-212">1</span><span class="sxs-lookup"><span data-stu-id="ab190-212">1</span></span> | <span data-ttu-id="ab190-213">14 </span><span class="sxs-lookup"><span data-stu-id="ab190-213">14</span></span> |
| <span data-ttu-id="ab190-214">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-214">Send to conversation</span></span> | <span data-ttu-id="ab190-215">2</span><span class="sxs-lookup"><span data-stu-id="ab190-215">2</span></span> | <span data-ttu-id="ab190-216">16 </span><span class="sxs-lookup"><span data-stu-id="ab190-216">16</span></span> |
| <span data-ttu-id="ab190-217">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-217">Create conversation</span></span> | <span data-ttu-id="ab190-218">1</span><span class="sxs-lookup"><span data-stu-id="ab190-218">1</span></span> | <span data-ttu-id="ab190-219">14 </span><span class="sxs-lookup"><span data-stu-id="ab190-219">14</span></span> |
| <span data-ttu-id="ab190-220">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-220">Create conversation</span></span> | <span data-ttu-id="ab190-221">2</span><span class="sxs-lookup"><span data-stu-id="ab190-221">2</span></span> | <span data-ttu-id="ab190-222">16 </span><span class="sxs-lookup"><span data-stu-id="ab190-222">16</span></span> |
| <span data-ttu-id="ab190-223">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-223">Create conversation</span></span>| <span data-ttu-id="ab190-224">1</span><span class="sxs-lookup"><span data-stu-id="ab190-224">1</span></span> | <span data-ttu-id="ab190-225">14 </span><span class="sxs-lookup"><span data-stu-id="ab190-225">14</span></span> |
| <span data-ttu-id="ab190-226">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-226">Create conversation</span></span>| <span data-ttu-id="ab190-227">2</span><span class="sxs-lookup"><span data-stu-id="ab190-227">2</span></span> | <span data-ttu-id="ab190-228">16 </span><span class="sxs-lookup"><span data-stu-id="ab190-228">16</span></span> |
| <span data-ttu-id="ab190-229">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-229">Get conversation members</span></span>| <span data-ttu-id="ab190-230">1</span><span class="sxs-lookup"><span data-stu-id="ab190-230">1</span></span> | <span data-ttu-id="ab190-231">28</span><span class="sxs-lookup"><span data-stu-id="ab190-231">28</span></span> |
| <span data-ttu-id="ab190-232">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="ab190-232">Get conversation members</span></span>| <span data-ttu-id="ab190-233">2</span><span class="sxs-lookup"><span data-stu-id="ab190-233">2</span></span> | <span data-ttu-id="ab190-234">32</span><span class="sxs-lookup"><span data-stu-id="ab190-234">32</span></span> |
| <span data-ttu-id="ab190-235">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="ab190-235">Get conversations</span></span> | <span data-ttu-id="ab190-236">1</span><span class="sxs-lookup"><span data-stu-id="ab190-236">1</span></span> | <span data-ttu-id="ab190-237">28</span><span class="sxs-lookup"><span data-stu-id="ab190-237">28</span></span> |
| <span data-ttu-id="ab190-238">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="ab190-238">Get conversations</span></span> | <span data-ttu-id="ab190-239">2</span><span class="sxs-lookup"><span data-stu-id="ab190-239">2</span></span> | <span data-ttu-id="ab190-240">32</span><span class="sxs-lookup"><span data-stu-id="ab190-240">32</span></span> |

## <a name="next-step"></a><span data-ttu-id="ab190-241">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ab190-241">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab190-242">Bots de chamadas e reuniões</span><span class="sxs-lookup"><span data-stu-id="ab190-242">Calls and meetings bots</span></span>](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

