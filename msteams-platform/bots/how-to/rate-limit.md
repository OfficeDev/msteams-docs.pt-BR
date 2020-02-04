---
title: Limitação de taxa
description: Limitação de taxa e práticas recomendadas no Microsoft Teams
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 4e9efab539ec7817d259fd6c149c438ba02e3ce5
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672578"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="9a29b-104">Otimize seu bot: limitação de taxa e práticas recomendadas no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9a29b-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="9a29b-105">Como princípio geral, seu aplicativo deve limitar o número de mensagens postadas para uma conversa de canal ou chat individual.</span><span class="sxs-lookup"><span data-stu-id="9a29b-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="9a29b-106">Isso garante uma experiência ideal que não considera "spam" para seus usuários finais.</span><span class="sxs-lookup"><span data-stu-id="9a29b-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="9a29b-107">Para proteger o Microsoft Teams e seus usuários, as solicitações de APIs de bot limitam as solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="9a29b-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="9a29b-108">Os aplicativos que ultrapassarem esse limite receberão um status de `HTTP 429 Too Many Requests` erro.</span><span class="sxs-lookup"><span data-stu-id="9a29b-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="9a29b-109">Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo envio de mensagens, enumerações de canal e buscas de lista.</span><span class="sxs-lookup"><span data-stu-id="9a29b-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="9a29b-110">Como os valores exatos dos limites de taxa estão sujeitos a alterações, recomendamos que seu aplicativo implemente o comportamento de retrocesso `HTTP 429 Too Many Requests`apropriado quando a API retornar.</span><span class="sxs-lookup"><span data-stu-id="9a29b-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="9a29b-111">Limites de taxa de manipulação</span><span class="sxs-lookup"><span data-stu-id="9a29b-111">Handling rate limits</span></span>

<span data-ttu-id="9a29b-112">Ao emitir uma operação de SDK do bot Builder, você pode `Microsoft.Rest.HttpOperationException` lidar e verificar o código de status.</span><span class="sxs-lookup"><span data-stu-id="9a29b-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="9a29b-113">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="9a29b-113">Best practices</span></span>

<span data-ttu-id="9a29b-114">Em geral, você deve tomar precauções simples para evitar o `HTTP 429` recebimento de respostas.</span><span class="sxs-lookup"><span data-stu-id="9a29b-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="9a29b-115">Por exemplo, evite emitir várias solicitações à mesma conversa pessoal ou de canal.</span><span class="sxs-lookup"><span data-stu-id="9a29b-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="9a29b-116">Em vez disso, considere o envio em lote das solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="9a29b-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="9a29b-117">Usar uma retirada exponencial com uma tremulação aleatória é a maneira recomendada de lidar com 429s.</span><span class="sxs-lookup"><span data-stu-id="9a29b-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="9a29b-118">Isso garante que várias solicitações não introduzam colisões em tentativas.</span><span class="sxs-lookup"><span data-stu-id="9a29b-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="9a29b-119">Exemplo: detectando exceções transitórias</span><span class="sxs-lookup"><span data-stu-id="9a29b-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="9a29b-120">Aqui está um exemplo usando a retirada exponencial por meio do bloco de aplicativo de tratamento de falhas transitório.</span><span class="sxs-lookup"><span data-stu-id="9a29b-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="9a29b-121">Você pode executar retrocesso e novas tentativas usando [bibliotecas transitórias de tratamento de falhas](/previous-versions/msp-n-p/hh680901(v=pandp.50)).</span><span class="sxs-lookup"><span data-stu-id="9a29b-121">You can perform backoff and retries using [Transient Fault Handling libraries](/previous-versions/msp-n-p/hh680901(v=pandp.50)).</span></span> <span data-ttu-id="9a29b-122">Para obter diretrizes sobre como obter e instalar o pacote NuGet, confira [adicionando o bloqueio de aplicativo de tratamento de falhas transitório à sua solução](/previous-versions/msp-n-p/hh680891(v=pandp.50))</span><span class="sxs-lookup"><span data-stu-id="9a29b-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/hh680891(v=pandp.50))</span></span>

```csharp
public class BotSdkTransientExceptionDetectionStrategy : ITransientErrorDetectionStrategy
{
    // List of error codes to retry on
    List<int> transientErrorStatusCodes = new List<int>() { 429 };

    public bool IsTransient(Exception ex)
    {
        var httpOperationException = ex as HttpOperationException;
        if (httpOperationException != null)
        {
            return httpOperationException.Response != null &&
                    transientErrorStatusCodes.Contains((int) httpOperationException.Response.StatusCode);
        }

        return false;
    }
}
```

## <a name="example-backoff"></a><span data-ttu-id="9a29b-123">Exemplo: retrocesso</span><span class="sxs-lookup"><span data-stu-id="9a29b-123">Example: backoff</span></span>

<span data-ttu-id="9a29b-124">Além de detectar limites de taxa, você também pode executar uma retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="9a29b-124">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

```csharp
/**
* The first parameter specifies the number of retries before failing the operation.
* The second parameter specifies the minimum and maximum backoff time respectively.
* The last parameter is used to add a randomized  +/- 20% delta to avoid numerous clients retrying simultaneously.
*/
var exponentialBackoffRetryStrategy = new ExponentialBackoff(3, TimeSpan.FromSeconds(2),
                        TimeSpan.FromSeconds(20), TimeSpan.FromSeconds(1));


// Define the Retry Policy
var retryPolicy = new RetryPolicy(new BotSdkTransientExceptionDetectionStrategy(), fixedIntervalRetryStrategy);

//Execute any bot sdk action
await retryPolicy.ExecuteAsync(() => connector.Conversations.ReplyToActivityAsync((Activity)reply)).ConfigureAwait(false);
```

<span data-ttu-id="9a29b-125">Você também pode executar uma `System.Action` execução de método com a política de repetição descrita acima.</span><span class="sxs-lookup"><span data-stu-id="9a29b-125">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="9a29b-126">A biblioteca de referência também permite que você especifique um intervalo fixo ou um mecanismo de retrocesso linear.</span><span class="sxs-lookup"><span data-stu-id="9a29b-126">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="9a29b-127">Recomendamos armazenar o valor e a estratégia em um arquivo de configuração para ajustar e ajustar os valores no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9a29b-127">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="9a29b-128">Para obter mais informações, confira este guia útil em vários padrões de repetição: [padrão de repetição](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="9a29b-128">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="9a29b-129">Por bot por limite de thread</span><span class="sxs-lookup"><span data-stu-id="9a29b-129">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="9a29b-130">A divisão de mensagens no nível de serviço resultará em um maior número de solicitações esperadas por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="9a29b-130">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="9a29b-131">Se você estiver preocupado com a abordagem dos limites, você deve implementar a estratégia de retrocesso descrita acima.</span><span class="sxs-lookup"><span data-stu-id="9a29b-131">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="9a29b-132">Os valores fornecidos abaixo são apenas para previsão.</span><span class="sxs-lookup"><span data-stu-id="9a29b-132">The values provided below are for estimation only.</span></span>

<span data-ttu-id="9a29b-133">Esse limite controla o tráfego que um bot tem permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="9a29b-133">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="9a29b-134">Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="9a29b-134">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="9a29b-135">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="9a29b-135">**Scenario**</span></span> | <span data-ttu-id="9a29b-136">**Período de tempo (seg)**</span><span class="sxs-lookup"><span data-stu-id="9a29b-136">**Time-period (sec)**</span></span> | <span data-ttu-id="9a29b-137">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="9a29b-137">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9a29b-138">NewMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-138">NewMessage</span></span> | <span data-ttu-id="9a29b-139">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-139">1</span></span> | <span data-ttu-id="9a29b-140">7 </span><span class="sxs-lookup"><span data-stu-id="9a29b-140">7</span></span> |
| <span data-ttu-id="9a29b-141">NewMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-141">NewMessage</span></span> | <span data-ttu-id="9a29b-142">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-142">2</span></span> | <span data-ttu-id="9a29b-143">8 </span><span class="sxs-lookup"><span data-stu-id="9a29b-143">8</span></span> |
| <span data-ttu-id="9a29b-144">NewMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-144">NewMessage</span></span> | <span data-ttu-id="9a29b-145">até</span><span class="sxs-lookup"><span data-stu-id="9a29b-145">30</span></span> | <span data-ttu-id="9a29b-146">60</span><span class="sxs-lookup"><span data-stu-id="9a29b-146">60</span></span> |
| <span data-ttu-id="9a29b-147">NewMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-147">NewMessage</span></span> | <span data-ttu-id="9a29b-148">3600</span><span class="sxs-lookup"><span data-stu-id="9a29b-148">3600</span></span> | <span data-ttu-id="9a29b-149">1800</span><span class="sxs-lookup"><span data-stu-id="9a29b-149">1800</span></span> |
| <span data-ttu-id="9a29b-150">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-150">UpdateMessage</span></span> | <span data-ttu-id="9a29b-151">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-151">1</span></span> | <span data-ttu-id="9a29b-152">7 </span><span class="sxs-lookup"><span data-stu-id="9a29b-152">7</span></span> |
| <span data-ttu-id="9a29b-153">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-153">UpdateMessage</span></span> | <span data-ttu-id="9a29b-154">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-154">2</span></span> | <span data-ttu-id="9a29b-155">8 </span><span class="sxs-lookup"><span data-stu-id="9a29b-155">8</span></span> |
| <span data-ttu-id="9a29b-156">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-156">UpdateMessage</span></span> | <span data-ttu-id="9a29b-157">até</span><span class="sxs-lookup"><span data-stu-id="9a29b-157">30</span></span> | <span data-ttu-id="9a29b-158">60</span><span class="sxs-lookup"><span data-stu-id="9a29b-158">60</span></span> |
| <span data-ttu-id="9a29b-159">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-159">UpdateMessage</span></span> | <span data-ttu-id="9a29b-160">3600</span><span class="sxs-lookup"><span data-stu-id="9a29b-160">3600</span></span> | <span data-ttu-id="9a29b-161">1800</span><span class="sxs-lookup"><span data-stu-id="9a29b-161">1800</span></span> |
| <span data-ttu-id="9a29b-162">NewThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-162">NewThread</span></span> | <span data-ttu-id="9a29b-163">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-163">1</span></span> | <span data-ttu-id="9a29b-164">7 </span><span class="sxs-lookup"><span data-stu-id="9a29b-164">7</span></span> |
| <span data-ttu-id="9a29b-165">NewThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-165">NewThread</span></span> | <span data-ttu-id="9a29b-166">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-166">2</span></span> | <span data-ttu-id="9a29b-167">8 </span><span class="sxs-lookup"><span data-stu-id="9a29b-167">8</span></span> |
| <span data-ttu-id="9a29b-168">NewThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-168">NewThread</span></span> | <span data-ttu-id="9a29b-169">até</span><span class="sxs-lookup"><span data-stu-id="9a29b-169">30</span></span> | <span data-ttu-id="9a29b-170">60</span><span class="sxs-lookup"><span data-stu-id="9a29b-170">60</span></span> |
| <span data-ttu-id="9a29b-171">NewThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-171">NewThread</span></span> | <span data-ttu-id="9a29b-172">3600</span><span class="sxs-lookup"><span data-stu-id="9a29b-172">3600</span></span> | <span data-ttu-id="9a29b-173">1800</span><span class="sxs-lookup"><span data-stu-id="9a29b-173">1800</span></span> |
| <span data-ttu-id="9a29b-174">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="9a29b-174">GetThreadMembers</span></span> | <span data-ttu-id="9a29b-175">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-175">1</span></span> | <span data-ttu-id="9a29b-176">14 </span><span class="sxs-lookup"><span data-stu-id="9a29b-176">14</span></span> |
| <span data-ttu-id="9a29b-177">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="9a29b-177">GetThreadMembers</span></span> | <span data-ttu-id="9a29b-178">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-178">2</span></span> | <span data-ttu-id="9a29b-179">16 </span><span class="sxs-lookup"><span data-stu-id="9a29b-179">16</span></span> |
| <span data-ttu-id="9a29b-180">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="9a29b-180">GetThreadMembers</span></span> | <span data-ttu-id="9a29b-181">até</span><span class="sxs-lookup"><span data-stu-id="9a29b-181">30</span></span> | <span data-ttu-id="9a29b-182">120</span><span class="sxs-lookup"><span data-stu-id="9a29b-182">120</span></span> |
| <span data-ttu-id="9a29b-183">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="9a29b-183">GetThreadMembers</span></span> | <span data-ttu-id="9a29b-184">3600</span><span class="sxs-lookup"><span data-stu-id="9a29b-184">3600</span></span> | <span data-ttu-id="9a29b-185">3600</span><span class="sxs-lookup"><span data-stu-id="9a29b-185">3600</span></span> |
| <span data-ttu-id="9a29b-186">GetThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-186">GetThread</span></span> | <span data-ttu-id="9a29b-187">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-187">1</span></span> | <span data-ttu-id="9a29b-188">14 </span><span class="sxs-lookup"><span data-stu-id="9a29b-188">14</span></span> |
| <span data-ttu-id="9a29b-189">GetThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-189">GetThread</span></span> | <span data-ttu-id="9a29b-190">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-190">2</span></span> | <span data-ttu-id="9a29b-191">16 </span><span class="sxs-lookup"><span data-stu-id="9a29b-191">16</span></span> |
| <span data-ttu-id="9a29b-192">GetThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-192">GetThread</span></span> | <span data-ttu-id="9a29b-193">até</span><span class="sxs-lookup"><span data-stu-id="9a29b-193">30</span></span> | <span data-ttu-id="9a29b-194">120</span><span class="sxs-lookup"><span data-stu-id="9a29b-194">120</span></span> |
| <span data-ttu-id="9a29b-195">GetThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-195">GetThread</span></span> | <span data-ttu-id="9a29b-196">3600</span><span class="sxs-lookup"><span data-stu-id="9a29b-196">3600</span></span> | <span data-ttu-id="9a29b-197">3600</span><span class="sxs-lookup"><span data-stu-id="9a29b-197">3600</span></span> |

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="9a29b-198">Limite por thread para todos os bots</span><span class="sxs-lookup"><span data-stu-id="9a29b-198">Per thread limit for all bots</span></span>

<span data-ttu-id="9a29b-199">Esse limite controla o tráfego que todos os bots podem gerar através de uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="9a29b-199">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="9a29b-200">Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="9a29b-200">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="9a29b-201">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="9a29b-201">**Scenario**</span></span> | <span data-ttu-id="9a29b-202">**Período de tempo (seg)**</span><span class="sxs-lookup"><span data-stu-id="9a29b-202">**Time-period (sec)**</span></span> | <span data-ttu-id="9a29b-203">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="9a29b-203">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9a29b-204">NewMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-204">NewMessage</span></span> | <span data-ttu-id="9a29b-205">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-205">1</span></span> | <span data-ttu-id="9a29b-206">14 </span><span class="sxs-lookup"><span data-stu-id="9a29b-206">14</span></span> |
| <span data-ttu-id="9a29b-207">NewMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-207">NewMessage</span></span> | <span data-ttu-id="9a29b-208">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-208">2</span></span> | <span data-ttu-id="9a29b-209">16 </span><span class="sxs-lookup"><span data-stu-id="9a29b-209">16</span></span> |
| <span data-ttu-id="9a29b-210">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-210">UpdateMessage</span></span> | <span data-ttu-id="9a29b-211">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-211">1</span></span> | <span data-ttu-id="9a29b-212">14 </span><span class="sxs-lookup"><span data-stu-id="9a29b-212">14</span></span> |
| <span data-ttu-id="9a29b-213">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="9a29b-213">UpdateMessage</span></span> | <span data-ttu-id="9a29b-214">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-214">2</span></span> | <span data-ttu-id="9a29b-215">16 </span><span class="sxs-lookup"><span data-stu-id="9a29b-215">16</span></span> |
| <span data-ttu-id="9a29b-216">NewThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-216">NewThread</span></span> | <span data-ttu-id="9a29b-217">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-217">1</span></span> | <span data-ttu-id="9a29b-218">14 </span><span class="sxs-lookup"><span data-stu-id="9a29b-218">14</span></span> |
| <span data-ttu-id="9a29b-219">NewThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-219">NewThread</span></span> | <span data-ttu-id="9a29b-220">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-220">2</span></span> | <span data-ttu-id="9a29b-221">16 </span><span class="sxs-lookup"><span data-stu-id="9a29b-221">16</span></span> |
| <span data-ttu-id="9a29b-222">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="9a29b-222">GetThreadMembers</span></span> | <span data-ttu-id="9a29b-223">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-223">1</span></span> | <span data-ttu-id="9a29b-224">28</span><span class="sxs-lookup"><span data-stu-id="9a29b-224">28</span></span> |
| <span data-ttu-id="9a29b-225">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="9a29b-225">GetThreadMembers</span></span> | <span data-ttu-id="9a29b-226">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-226">2</span></span> | <span data-ttu-id="9a29b-227">32</span><span class="sxs-lookup"><span data-stu-id="9a29b-227">32</span></span> |
| <span data-ttu-id="9a29b-228">GetThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-228">GetThread</span></span> | <span data-ttu-id="9a29b-229">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-229">1</span></span> | <span data-ttu-id="9a29b-230">28</span><span class="sxs-lookup"><span data-stu-id="9a29b-230">28</span></span> |
| <span data-ttu-id="9a29b-231">GetThread</span><span class="sxs-lookup"><span data-stu-id="9a29b-231">GetThread</span></span> | <span data-ttu-id="9a29b-232">2 </span><span class="sxs-lookup"><span data-stu-id="9a29b-232">2</span></span> | <span data-ttu-id="9a29b-233">32</span><span class="sxs-lookup"><span data-stu-id="9a29b-233">32</span></span> |

## <a name="bot-per-data-center-limit"></a><span data-ttu-id="9a29b-234">Bot por limite de data center</span><span class="sxs-lookup"><span data-stu-id="9a29b-234">Bot per data center limit</span></span>

<span data-ttu-id="9a29b-235">Esse limite controla o tráfego que um bot tem permissão para gerar em todos os threads em um Data Center (entre vários locatários).</span><span class="sxs-lookup"><span data-stu-id="9a29b-235">This limit controls the traffic that a bot is allowed to generate across all threads in a data center (across multiple tenants).</span></span>

|<span data-ttu-id="9a29b-236">**Período de tempo (seg)**</span><span class="sxs-lookup"><span data-stu-id="9a29b-236">**Time-period (sec)**</span></span> | <span data-ttu-id="9a29b-237">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="9a29b-237">**Max allowed operations**</span></span> |
| --- | --- |
| <span data-ttu-id="9a29b-238">1 </span><span class="sxs-lookup"><span data-stu-id="9a29b-238">1</span></span> | <span data-ttu-id="9a29b-239">508</span><span class="sxs-lookup"><span data-stu-id="9a29b-239">20</span></span> |
| <span data-ttu-id="9a29b-240">1800</span><span class="sxs-lookup"><span data-stu-id="9a29b-240">1800</span></span> | <span data-ttu-id="9a29b-241">8000</span><span class="sxs-lookup"><span data-stu-id="9a29b-241">8000</span></span> |
| <span data-ttu-id="9a29b-242">3600</span><span class="sxs-lookup"><span data-stu-id="9a29b-242">3600</span></span> | <span data-ttu-id="9a29b-243">15000</span><span class="sxs-lookup"><span data-stu-id="9a29b-243">15000</span></span> |
