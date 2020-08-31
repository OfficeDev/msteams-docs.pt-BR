---
title: Limitação de taxa
description: Limitação de taxa e práticas recomendadas no Microsoft Teams
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 2e401b59df075688cb6d459a881e6b813f2cf8e6
ms.sourcegitcommit: b3962a7b36f260aef1af9124d14d71ae08b01ac4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2020
ms.locfileid: "47303707"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="b02a7-104">Otimize seu bot: limitação de taxa e práticas recomendadas no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b02a7-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="b02a7-105">Como princípio geral, seu aplicativo deve limitar o número de mensagens postadas para uma conversa de canal ou chat individual.</span><span class="sxs-lookup"><span data-stu-id="b02a7-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="b02a7-106">Isso garante uma experiência ideal que não considera "spam" para seus usuários finais.</span><span class="sxs-lookup"><span data-stu-id="b02a7-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="b02a7-107">Para proteger o Microsoft Teams e seus usuários, as solicitações de APIs de bot limitam as solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="b02a7-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="b02a7-108">Os aplicativos que ultrapassarem esse limite receberão um `HTTP 429 Too Many Requests` status de erro.</span><span class="sxs-lookup"><span data-stu-id="b02a7-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="b02a7-109">Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo envio de mensagens, enumerações de canal e buscas de lista.</span><span class="sxs-lookup"><span data-stu-id="b02a7-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="b02a7-110">Como os valores exatos dos limites de taxa estão sujeitos a alterações, recomendamos que seu aplicativo implemente o comportamento de retrocesso apropriado quando a API retornar `HTTP 429 Too Many Requests` .</span><span class="sxs-lookup"><span data-stu-id="b02a7-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="b02a7-111">Limites de taxa de manipulação</span><span class="sxs-lookup"><span data-stu-id="b02a7-111">Handling rate limits</span></span>

<span data-ttu-id="b02a7-112">Ao emitir uma operação de SDK do bot Builder, você pode lidar `Microsoft.Rest.HttpOperationException` e verificar o código de status.</span><span class="sxs-lookup"><span data-stu-id="b02a7-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="b02a7-113">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b02a7-113">Best practices</span></span>

<span data-ttu-id="b02a7-114">Em geral, você deve tomar precauções simples para evitar o recebimento de `HTTP 429` respostas.</span><span class="sxs-lookup"><span data-stu-id="b02a7-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="b02a7-115">Por exemplo, evite emitir várias solicitações à mesma conversa pessoal ou de canal.</span><span class="sxs-lookup"><span data-stu-id="b02a7-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="b02a7-116">Em vez disso, considere o envio em lote das solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="b02a7-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="b02a7-117">Usar uma retirada exponencial com uma tremulação aleatória é a maneira recomendada de lidar com 429s.</span><span class="sxs-lookup"><span data-stu-id="b02a7-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="b02a7-118">Isso garante que várias solicitações não introduzam colisões em tentativas.</span><span class="sxs-lookup"><span data-stu-id="b02a7-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="b02a7-119">Exemplo: detectando exceções transitórias</span><span class="sxs-lookup"><span data-stu-id="b02a7-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="b02a7-120">Aqui está um exemplo usando a retirada exponencial por meio do bloco de aplicativo de tratamento de falhas transitório.</span><span class="sxs-lookup"><span data-stu-id="b02a7-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="b02a7-121">Você pode executar retrocesso e novas tentativas usando a [manipulação de falhas transitória](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="b02a7-121">You can perform backoff and retries using [Transient Fault Handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="b02a7-122">Para obter diretrizes sobre como obter e instalar o pacote NuGet, confira [adicionando o bloqueio de aplicativo de tratamento de falhas transitório à sua solução](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span><span class="sxs-lookup"><span data-stu-id="b02a7-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span></span> <span data-ttu-id="b02a7-123">*Confira também* o [tratamento transitório de falhas](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="b02a7-123">*See also* [Transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

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

## <a name="example-backoff"></a><span data-ttu-id="b02a7-124">Exemplo: retrocesso</span><span class="sxs-lookup"><span data-stu-id="b02a7-124">Example: backoff</span></span>

<span data-ttu-id="b02a7-125">Além de detectar limites de taxa, você também pode executar uma retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="b02a7-125">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

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

<span data-ttu-id="b02a7-126">Você também pode executar uma `System.Action` execução de método com a política de repetição descrita acima.</span><span class="sxs-lookup"><span data-stu-id="b02a7-126">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="b02a7-127">A biblioteca de referência também permite que você especifique um intervalo fixo ou um mecanismo de retrocesso linear.</span><span class="sxs-lookup"><span data-stu-id="b02a7-127">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="b02a7-128">Recomendamos armazenar o valor e a estratégia em um arquivo de configuração para ajustar e ajustar os valores no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b02a7-128">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="b02a7-129">Para obter mais informações, confira este guia útil em vários padrões de repetição: [padrão de repetição](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="b02a7-129">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="b02a7-130">Por bot por limite de thread</span><span class="sxs-lookup"><span data-stu-id="b02a7-130">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="b02a7-131">A divisão de mensagens no nível de serviço resultará em um maior número de solicitações esperadas por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="b02a7-131">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="b02a7-132">Se você estiver preocupado com a abordagem dos limites, você deve implementar a estratégia de retrocesso descrita acima.</span><span class="sxs-lookup"><span data-stu-id="b02a7-132">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="b02a7-133">Os valores fornecidos abaixo são apenas para previsão.</span><span class="sxs-lookup"><span data-stu-id="b02a7-133">The values provided below are for estimation only.</span></span>

<span data-ttu-id="b02a7-134">Esse limite controla o tráfego que um bot tem permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="b02a7-134">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="b02a7-135">Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="b02a7-135">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="b02a7-136">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="b02a7-136">**Scenario**</span></span> | <span data-ttu-id="b02a7-137">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="b02a7-137">**Time-period (sec)**</span></span> | <span data-ttu-id="b02a7-138">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="b02a7-138">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b02a7-139">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-139">Send to Conversation</span></span> | <span data-ttu-id="b02a7-140">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-140">1</span></span> | <span data-ttu-id="b02a7-141">7 </span><span class="sxs-lookup"><span data-stu-id="b02a7-141">7</span></span> |
| <span data-ttu-id="b02a7-142">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-142">Send to Conversation</span></span> | <span data-ttu-id="b02a7-143">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-143">2</span></span> | <span data-ttu-id="b02a7-144">8 </span><span class="sxs-lookup"><span data-stu-id="b02a7-144">8</span></span> |
| <span data-ttu-id="b02a7-145">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-145">Send to Conversation</span></span> | <span data-ttu-id="b02a7-146">até</span><span class="sxs-lookup"><span data-stu-id="b02a7-146">30</span></span> | <span data-ttu-id="b02a7-147">60</span><span class="sxs-lookup"><span data-stu-id="b02a7-147">60</span></span> |
| <span data-ttu-id="b02a7-148">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-148">Send to Conversation</span></span> | <span data-ttu-id="b02a7-149">3600</span><span class="sxs-lookup"><span data-stu-id="b02a7-149">3600</span></span> | <span data-ttu-id="b02a7-150">1800</span><span class="sxs-lookup"><span data-stu-id="b02a7-150">1800</span></span> |
| <span data-ttu-id="b02a7-151">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-151">Create Conversation</span></span> | <span data-ttu-id="b02a7-152">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-152">1</span></span> | <span data-ttu-id="b02a7-153">7 </span><span class="sxs-lookup"><span data-stu-id="b02a7-153">7</span></span> |
| <span data-ttu-id="b02a7-154">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-154">Create Conversation</span></span> | <span data-ttu-id="b02a7-155">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-155">2</span></span> | <span data-ttu-id="b02a7-156">8 </span><span class="sxs-lookup"><span data-stu-id="b02a7-156">8</span></span> |
| <span data-ttu-id="b02a7-157">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-157">Create Conversation</span></span> | <span data-ttu-id="b02a7-158">até</span><span class="sxs-lookup"><span data-stu-id="b02a7-158">30</span></span> | <span data-ttu-id="b02a7-159">60</span><span class="sxs-lookup"><span data-stu-id="b02a7-159">60</span></span> |
| <span data-ttu-id="b02a7-160">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-160">Create Conversation</span></span> | <span data-ttu-id="b02a7-161">3600</span><span class="sxs-lookup"><span data-stu-id="b02a7-161">3600</span></span> | <span data-ttu-id="b02a7-162">1800</span><span class="sxs-lookup"><span data-stu-id="b02a7-162">1800</span></span> |
| <span data-ttu-id="b02a7-163">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-163">Get Conversation Members</span></span>| <span data-ttu-id="b02a7-164">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-164">1</span></span> | <span data-ttu-id="b02a7-165">14 </span><span class="sxs-lookup"><span data-stu-id="b02a7-165">14</span></span> |
| <span data-ttu-id="b02a7-166">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-166">Get Conversation Members</span></span>| <span data-ttu-id="b02a7-167">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-167">2</span></span> | <span data-ttu-id="b02a7-168">16 </span><span class="sxs-lookup"><span data-stu-id="b02a7-168">16</span></span> |
| <span data-ttu-id="b02a7-169">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-169">Get Conversation Members</span></span>| <span data-ttu-id="b02a7-170">até</span><span class="sxs-lookup"><span data-stu-id="b02a7-170">30</span></span> | <span data-ttu-id="b02a7-171">120</span><span class="sxs-lookup"><span data-stu-id="b02a7-171">120</span></span> |
| <span data-ttu-id="b02a7-172">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-172">Get Conversation Members</span></span>| <span data-ttu-id="b02a7-173">3600</span><span class="sxs-lookup"><span data-stu-id="b02a7-173">3600</span></span> | <span data-ttu-id="b02a7-174">3600</span><span class="sxs-lookup"><span data-stu-id="b02a7-174">3600</span></span> |
| <span data-ttu-id="b02a7-175">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b02a7-175">Get Conversations</span></span> | <span data-ttu-id="b02a7-176">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-176">1</span></span> | <span data-ttu-id="b02a7-177">14 </span><span class="sxs-lookup"><span data-stu-id="b02a7-177">14</span></span> |
| <span data-ttu-id="b02a7-178">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b02a7-178">Get Conversations</span></span> | <span data-ttu-id="b02a7-179">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-179">2</span></span> | <span data-ttu-id="b02a7-180">16 </span><span class="sxs-lookup"><span data-stu-id="b02a7-180">16</span></span> |
| <span data-ttu-id="b02a7-181">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b02a7-181">Get Conversations</span></span> | <span data-ttu-id="b02a7-182">até</span><span class="sxs-lookup"><span data-stu-id="b02a7-182">30</span></span> | <span data-ttu-id="b02a7-183">120</span><span class="sxs-lookup"><span data-stu-id="b02a7-183">120</span></span> |
| <span data-ttu-id="b02a7-184">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b02a7-184">Get Conversations</span></span> | <span data-ttu-id="b02a7-185">3600</span><span class="sxs-lookup"><span data-stu-id="b02a7-185">3600</span></span> | <span data-ttu-id="b02a7-186">3600</span><span class="sxs-lookup"><span data-stu-id="b02a7-186">3600</span></span> |

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="b02a7-187">Limite por thread para todos os bots</span><span class="sxs-lookup"><span data-stu-id="b02a7-187">Per thread limit for all bots</span></span>

<span data-ttu-id="b02a7-188">Esse limite controla o tráfego que todos os bots podem gerar através de uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="b02a7-188">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="b02a7-189">Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="b02a7-189">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="b02a7-190">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="b02a7-190">**Scenario**</span></span> | <span data-ttu-id="b02a7-191">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="b02a7-191">**Time-period (sec)**</span></span> | <span data-ttu-id="b02a7-192">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="b02a7-192">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b02a7-193">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-193">Send to Conversation</span></span> | <span data-ttu-id="b02a7-194">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-194">1</span></span> | <span data-ttu-id="b02a7-195">14 </span><span class="sxs-lookup"><span data-stu-id="b02a7-195">14</span></span> |
| <span data-ttu-id="b02a7-196">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-196">Send to Conversation</span></span> | <span data-ttu-id="b02a7-197">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-197">2</span></span> | <span data-ttu-id="b02a7-198">16 </span><span class="sxs-lookup"><span data-stu-id="b02a7-198">16</span></span> |
| <span data-ttu-id="b02a7-199">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-199">Create Conversation</span></span> | <span data-ttu-id="b02a7-200">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-200">1</span></span> | <span data-ttu-id="b02a7-201">14 </span><span class="sxs-lookup"><span data-stu-id="b02a7-201">14</span></span> |
| <span data-ttu-id="b02a7-202">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-202">Create Conversation</span></span> | <span data-ttu-id="b02a7-203">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-203">2</span></span> | <span data-ttu-id="b02a7-204">16 </span><span class="sxs-lookup"><span data-stu-id="b02a7-204">16</span></span> |
| <span data-ttu-id="b02a7-205">Createconversation</span><span class="sxs-lookup"><span data-stu-id="b02a7-205">CreateConversation</span></span>| <span data-ttu-id="b02a7-206">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-206">1</span></span> | <span data-ttu-id="b02a7-207">14 </span><span class="sxs-lookup"><span data-stu-id="b02a7-207">14</span></span> |
| <span data-ttu-id="b02a7-208">Createconversation</span><span class="sxs-lookup"><span data-stu-id="b02a7-208">CreateConversation</span></span>| <span data-ttu-id="b02a7-209">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-209">2</span></span> | <span data-ttu-id="b02a7-210">16 </span><span class="sxs-lookup"><span data-stu-id="b02a7-210">16</span></span> |
| <span data-ttu-id="b02a7-211">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-211">Get Conversation Members</span></span>| <span data-ttu-id="b02a7-212">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-212">1</span></span> | <span data-ttu-id="b02a7-213">28</span><span class="sxs-lookup"><span data-stu-id="b02a7-213">28</span></span> |
| <span data-ttu-id="b02a7-214">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="b02a7-214">Get Conversation Members</span></span>| <span data-ttu-id="b02a7-215">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-215">2</span></span> | <span data-ttu-id="b02a7-216">32</span><span class="sxs-lookup"><span data-stu-id="b02a7-216">32</span></span> |
| <span data-ttu-id="b02a7-217">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b02a7-217">Get Conversations</span></span> | <span data-ttu-id="b02a7-218">1 </span><span class="sxs-lookup"><span data-stu-id="b02a7-218">1</span></span> | <span data-ttu-id="b02a7-219">28</span><span class="sxs-lookup"><span data-stu-id="b02a7-219">28</span></span> |
| <span data-ttu-id="b02a7-220">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="b02a7-220">Get Conversations</span></span> | <span data-ttu-id="b02a7-221">2 </span><span class="sxs-lookup"><span data-stu-id="b02a7-221">2</span></span> | <span data-ttu-id="b02a7-222">32</span><span class="sxs-lookup"><span data-stu-id="b02a7-222">32</span></span> |
