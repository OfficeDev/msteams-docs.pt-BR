---
title: Limitação de taxa
description: Limitação de taxa e práticas recomendadas no Microsoft Teams
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 9b244053d42aaddaf48c798e401438b614b0e1bd
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "44800985"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="b1c1e-104">Otimize seu bot: limitação de taxa e práticas recomendadas no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b1c1e-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="b1c1e-105">Como princípio geral, seu aplicativo deve limitar o número de mensagens postadas para uma conversa de canal ou chat individual.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="b1c1e-106">Isso garante uma experiência ideal que não considera "spam" para seus usuários finais.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="b1c1e-107">Para proteger o Microsoft Teams e seus usuários, as solicitações de APIs de bot limitam as solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="b1c1e-108">Os aplicativos que ultrapassarem esse limite receberão um `HTTP 429 Too Many Requests` status de erro.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="b1c1e-109">Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo envio de mensagens, enumerações de canal e buscas de lista.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="b1c1e-110">Como os valores exatos dos limites de taxa estão sujeitos a alterações, recomendamos que seu aplicativo implemente o comportamento de retrocesso apropriado quando a API retornar `HTTP 429 Too Many Requests` .</span><span class="sxs-lookup"><span data-stu-id="b1c1e-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="b1c1e-111">Limites de taxa de manipulação</span><span class="sxs-lookup"><span data-stu-id="b1c1e-111">Handling rate limits</span></span>

<span data-ttu-id="b1c1e-112">Ao emitir uma operação de SDK do bot Builder, você pode lidar `Microsoft.Rest.HttpOperationException` e verificar o código de status.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="b1c1e-113">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-113">Best practices</span></span>

<span data-ttu-id="b1c1e-114">Em geral, você deve tomar precauções simples para evitar o recebimento de `HTTP 429` respostas.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="b1c1e-115">Por exemplo, evite emitir várias solicitações à mesma conversa pessoal ou de canal.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="b1c1e-116">Em vez disso, considere o envio em lote das solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="b1c1e-117">Usar uma retirada exponencial com uma tremulação aleatória é a maneira recomendada de lidar com 429s.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="b1c1e-118">Isso garante que várias solicitações não introduzam colisões em tentativas.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="b1c1e-119">Exemplo: detectando exceções transitórias</span><span class="sxs-lookup"><span data-stu-id="b1c1e-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="b1c1e-120">Aqui está um exemplo usando a retirada exponencial por meio do bloco de aplicativo de tratamento de falhas transitório.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="b1c1e-121">Você pode executar retrocesso e novas tentativas usando a [manipulação de falhas transitória](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="b1c1e-121">You can perform backoff and retries using [Transient Fault Handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="b1c1e-122">Para obter diretrizes sobre como obter e instalar o pacote NuGet, confira [adicionando o bloqueio de aplicativo de tratamento de falhas transitório à sua solução](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span><span class="sxs-lookup"><span data-stu-id="b1c1e-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span></span> <span data-ttu-id="b1c1e-123">*Confira também* o [tratamento transitório de falhas](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="b1c1e-123">*See also* [Transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

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

## <a name="example-backoff"></a><span data-ttu-id="b1c1e-124">Exemplo: retrocesso</span><span class="sxs-lookup"><span data-stu-id="b1c1e-124">Example: backoff</span></span>

<span data-ttu-id="b1c1e-125">Além de detectar limites de taxa, você também pode executar uma retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-125">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

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

<span data-ttu-id="b1c1e-126">Você também pode executar uma `System.Action` execução de método com a política de repetição descrita acima.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-126">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="b1c1e-127">A biblioteca de referência também permite que você especifique um intervalo fixo ou um mecanismo de retrocesso linear.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-127">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="b1c1e-128">Recomendamos armazenar o valor e a estratégia em um arquivo de configuração para ajustar e ajustar os valores no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-128">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="b1c1e-129">Para obter mais informações, confira este guia útil em vários padrões de repetição: [padrão de repetição](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="b1c1e-129">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="b1c1e-130">Por bot por limite de thread</span><span class="sxs-lookup"><span data-stu-id="b1c1e-130">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="b1c1e-131">A divisão de mensagens no nível de serviço resultará em um maior número de solicitações esperadas por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="b1c1e-131">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="b1c1e-132">Se você estiver preocupado com a abordagem dos limites, você deve implementar a estratégia de retrocesso descrita acima.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-132">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="b1c1e-133">Os valores fornecidos abaixo são apenas para previsão.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-133">The values provided below are for estimation only.</span></span>

<span data-ttu-id="b1c1e-134">Esse limite controla o tráfego que um bot tem permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-134">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="b1c1e-135">Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-135">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="b1c1e-136">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="b1c1e-136">**Scenario**</span></span> | <span data-ttu-id="b1c1e-137">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="b1c1e-137">**Time-period (sec)**</span></span> | <span data-ttu-id="b1c1e-138">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="b1c1e-138">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b1c1e-139">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-139">Send to Conversation</span></span> | <span data-ttu-id="b1c1e-140">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-140">1</span></span> | <span data-ttu-id="b1c1e-141">7 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-141">7</span></span> |
| <span data-ttu-id="b1c1e-142">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-142">Send to Conversation</span></span> | <span data-ttu-id="b1c1e-143">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-143">2</span></span> | <span data-ttu-id="b1c1e-144">8 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-144">8</span></span> |
| <span data-ttu-id="b1c1e-145">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-145">Send to Conversation</span></span> | <span data-ttu-id="b1c1e-146">até</span><span class="sxs-lookup"><span data-stu-id="b1c1e-146">30</span></span> | <span data-ttu-id="b1c1e-147">60</span><span class="sxs-lookup"><span data-stu-id="b1c1e-147">60</span></span> |
| <span data-ttu-id="b1c1e-148">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-148">Send to Conversation</span></span> | <span data-ttu-id="b1c1e-149">3600</span><span class="sxs-lookup"><span data-stu-id="b1c1e-149">3600</span></span> | <span data-ttu-id="b1c1e-150">1800</span><span class="sxs-lookup"><span data-stu-id="b1c1e-150">1800</span></span> |
| <span data-ttu-id="b1c1e-151">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-151">Create Conversation</span></span> | <span data-ttu-id="b1c1e-152">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-152">1</span></span> | <span data-ttu-id="b1c1e-153">7 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-153">7</span></span> |
| <span data-ttu-id="b1c1e-154">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-154">Create Conversation</span></span> | <span data-ttu-id="b1c1e-155">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-155">2</span></span> | <span data-ttu-id="b1c1e-156">8 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-156">8</span></span> |
| <span data-ttu-id="b1c1e-157">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-157">Create Conversation</span></span> | <span data-ttu-id="b1c1e-158">até</span><span class="sxs-lookup"><span data-stu-id="b1c1e-158">30</span></span> | <span data-ttu-id="b1c1e-159">60</span><span class="sxs-lookup"><span data-stu-id="b1c1e-159">60</span></span> |
| <span data-ttu-id="b1c1e-160">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-160">Create Conversation</span></span> | <span data-ttu-id="b1c1e-161">3600</span><span class="sxs-lookup"><span data-stu-id="b1c1e-161">3600</span></span> | <span data-ttu-id="b1c1e-162">1800</span><span class="sxs-lookup"><span data-stu-id="b1c1e-162">1800</span></span> |
| <span data-ttu-id="b1c1e-163">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-163">Get Conversation Members</span></span>| <span data-ttu-id="b1c1e-164">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-164">1</span></span> | <span data-ttu-id="b1c1e-165">14 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-165">14</span></span> |
| <span data-ttu-id="b1c1e-166">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-166">Get Conversation Members</span></span>| <span data-ttu-id="b1c1e-167">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-167">2</span></span> | <span data-ttu-id="b1c1e-168">16 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-168">16</span></span> |
| <span data-ttu-id="b1c1e-169">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-169">Get Conversation Members</span></span>| <span data-ttu-id="b1c1e-170">até</span><span class="sxs-lookup"><span data-stu-id="b1c1e-170">30</span></span> | <span data-ttu-id="b1c1e-171">120</span><span class="sxs-lookup"><span data-stu-id="b1c1e-171">120</span></span> |
| <span data-ttu-id="b1c1e-172">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-172">Get Conversation Members</span></span>| <span data-ttu-id="b1c1e-173">3600</span><span class="sxs-lookup"><span data-stu-id="b1c1e-173">3600</span></span> | <span data-ttu-id="b1c1e-174">3600</span><span class="sxs-lookup"><span data-stu-id="b1c1e-174">3600</span></span> |
| <span data-ttu-id="b1c1e-175">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-175">Get Conversations</span></span> | <span data-ttu-id="b1c1e-176">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-176">1</span></span> | <span data-ttu-id="b1c1e-177">14 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-177">14</span></span> |
| <span data-ttu-id="b1c1e-178">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-178">Get Conversations</span></span> | <span data-ttu-id="b1c1e-179">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-179">2</span></span> | <span data-ttu-id="b1c1e-180">16 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-180">16</span></span> |
| <span data-ttu-id="b1c1e-181">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-181">Get Conversations</span></span> | <span data-ttu-id="b1c1e-182">até</span><span class="sxs-lookup"><span data-stu-id="b1c1e-182">30</span></span> | <span data-ttu-id="b1c1e-183">120</span><span class="sxs-lookup"><span data-stu-id="b1c1e-183">120</span></span> |
| <span data-ttu-id="b1c1e-184">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-184">Get Conversations</span></span> | <span data-ttu-id="b1c1e-185">3600</span><span class="sxs-lookup"><span data-stu-id="b1c1e-185">3600</span></span> | <span data-ttu-id="b1c1e-186">3600</span><span class="sxs-lookup"><span data-stu-id="b1c1e-186">3600</span></span> |

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="b1c1e-187">Limite por thread para todos os bots</span><span class="sxs-lookup"><span data-stu-id="b1c1e-187">Per thread limit for all bots</span></span>

<span data-ttu-id="b1c1e-188">Esse limite controla o tráfego que todos os bots podem gerar através de uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-188">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="b1c1e-189">Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="b1c1e-189">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="b1c1e-190">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="b1c1e-190">**Scenario**</span></span> | <span data-ttu-id="b1c1e-191">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="b1c1e-191">**Time-period (sec)**</span></span> | <span data-ttu-id="b1c1e-192">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="b1c1e-192">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b1c1e-193">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-193">Send to Conversation</span></span> | <span data-ttu-id="b1c1e-194">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-194">1</span></span> | <span data-ttu-id="b1c1e-195">14 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-195">14</span></span> |
| <span data-ttu-id="b1c1e-196">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-196">Send to Conversation</span></span> | <span data-ttu-id="b1c1e-197">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-197">2</span></span> | <span data-ttu-id="b1c1e-198">16 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-198">16</span></span> |
| <span data-ttu-id="b1c1e-199">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-199">Create Conversation</span></span> | <span data-ttu-id="b1c1e-200">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-200">1</span></span> | <span data-ttu-id="b1c1e-201">14 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-201">14</span></span> |
| <span data-ttu-id="b1c1e-202">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-202">Create Conversation</span></span> | <span data-ttu-id="b1c1e-203">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-203">2</span></span> | <span data-ttu-id="b1c1e-204">16 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-204">16</span></span> |
| <span data-ttu-id="b1c1e-205">Createconversation</span><span class="sxs-lookup"><span data-stu-id="b1c1e-205">CreateConversation</span></span>| <span data-ttu-id="b1c1e-206">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-206">1</span></span> | <span data-ttu-id="b1c1e-207">14 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-207">14</span></span> |
| <span data-ttu-id="b1c1e-208">Createconversation</span><span class="sxs-lookup"><span data-stu-id="b1c1e-208">CreateConversation</span></span>| <span data-ttu-id="b1c1e-209">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-209">2</span></span> | <span data-ttu-id="b1c1e-210">16 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-210">16</span></span> |
| <span data-ttu-id="b1c1e-211">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-211">Get Conversation Members</span></span>| <span data-ttu-id="b1c1e-212">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-212">1</span></span> | <span data-ttu-id="b1c1e-213">28</span><span class="sxs-lookup"><span data-stu-id="b1c1e-213">28</span></span> |
| <span data-ttu-id="b1c1e-214">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b1c1e-214">Get Conversation Members</span></span>| <span data-ttu-id="b1c1e-215">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-215">2</span></span> | <span data-ttu-id="b1c1e-216">32</span><span class="sxs-lookup"><span data-stu-id="b1c1e-216">32</span></span> |
| <span data-ttu-id="b1c1e-217">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-217">Get Conversations</span></span> | <span data-ttu-id="b1c1e-218">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-218">1</span></span> | <span data-ttu-id="b1c1e-219">28</span><span class="sxs-lookup"><span data-stu-id="b1c1e-219">28</span></span> |
| <span data-ttu-id="b1c1e-220">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-220">Get Conversations</span></span> | <span data-ttu-id="b1c1e-221">duas</span><span class="sxs-lookup"><span data-stu-id="b1c1e-221">2</span></span> | <span data-ttu-id="b1c1e-222">32</span><span class="sxs-lookup"><span data-stu-id="b1c1e-222">32</span></span> |

## <a name="bot-per-data-center-limit"></a><span data-ttu-id="b1c1e-223">Bot por limite de data center</span><span class="sxs-lookup"><span data-stu-id="b1c1e-223">Bot per data center limit</span></span>

<span data-ttu-id="b1c1e-224">Esse limite controla o tráfego que um bot tem permissão para gerar em todos os threads em um Data Center (entre vários locatários).</span><span class="sxs-lookup"><span data-stu-id="b1c1e-224">This limit controls the traffic that a bot is allowed to generate across all threads in a data center (across multiple tenants).</span></span>

|<span data-ttu-id="b1c1e-225">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="b1c1e-225">**Time-period (sec)**</span></span> | <span data-ttu-id="b1c1e-226">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="b1c1e-226">**Max allowed operations**</span></span> |
| --- | --- |
| <span data-ttu-id="b1c1e-227">1 </span><span class="sxs-lookup"><span data-stu-id="b1c1e-227">1</span></span> | <span data-ttu-id="b1c1e-228">508</span><span class="sxs-lookup"><span data-stu-id="b1c1e-228">20</span></span> |
| <span data-ttu-id="b1c1e-229">1800</span><span class="sxs-lookup"><span data-stu-id="b1c1e-229">1800</span></span> | <span data-ttu-id="b1c1e-230">8000</span><span class="sxs-lookup"><span data-stu-id="b1c1e-230">8000</span></span> |
| <span data-ttu-id="b1c1e-231">3600</span><span class="sxs-lookup"><span data-stu-id="b1c1e-231">3600</span></span> | <span data-ttu-id="b1c1e-232">15000</span><span class="sxs-lookup"><span data-stu-id="b1c1e-232">15000</span></span> |
