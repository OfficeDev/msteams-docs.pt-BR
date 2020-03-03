---
title: Limitação de taxa
description: Limitação de taxa e práticas recomendadas no Microsoft Teams
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 145f65a7e17b833e11631dfc219d9f5732f43bc6
ms.sourcegitcommit: 6c692734a382865531a83b9ebd6f604212f484fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42371762"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="99f9b-104">Otimize seu bot: limitação de taxa e práticas recomendadas no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="99f9b-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="99f9b-105">Como princípio geral, seu aplicativo deve limitar o número de mensagens postadas para uma conversa de canal ou chat individual.</span><span class="sxs-lookup"><span data-stu-id="99f9b-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="99f9b-106">Isso garante uma experiência ideal que não considera "spam" para seus usuários finais.</span><span class="sxs-lookup"><span data-stu-id="99f9b-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="99f9b-107">Para proteger o Microsoft Teams e seus usuários, as solicitações de APIs de bot limitam as solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="99f9b-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="99f9b-108">Os aplicativos que ultrapassarem esse limite receberão um status de `HTTP 429 Too Many Requests` erro.</span><span class="sxs-lookup"><span data-stu-id="99f9b-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="99f9b-109">Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo envio de mensagens, enumerações de canal e buscas de lista.</span><span class="sxs-lookup"><span data-stu-id="99f9b-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="99f9b-110">Como os valores exatos dos limites de taxa estão sujeitos a alterações, recomendamos que seu aplicativo implemente o comportamento de retrocesso `HTTP 429 Too Many Requests`apropriado quando a API retornar.</span><span class="sxs-lookup"><span data-stu-id="99f9b-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="99f9b-111">Limites de taxa de manipulação</span><span class="sxs-lookup"><span data-stu-id="99f9b-111">Handling rate limits</span></span>

<span data-ttu-id="99f9b-112">Ao emitir uma operação de SDK do bot Builder, você pode `Microsoft.Rest.HttpOperationException` lidar e verificar o código de status.</span><span class="sxs-lookup"><span data-stu-id="99f9b-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="99f9b-113">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="99f9b-113">Best practices</span></span>

<span data-ttu-id="99f9b-114">Em geral, você deve tomar precauções simples para evitar o `HTTP 429` recebimento de respostas.</span><span class="sxs-lookup"><span data-stu-id="99f9b-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="99f9b-115">Por exemplo, evite emitir várias solicitações à mesma conversa pessoal ou de canal.</span><span class="sxs-lookup"><span data-stu-id="99f9b-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="99f9b-116">Em vez disso, considere o envio em lote das solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="99f9b-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="99f9b-117">Usar uma retirada exponencial com uma tremulação aleatória é a maneira recomendada de lidar com 429s.</span><span class="sxs-lookup"><span data-stu-id="99f9b-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="99f9b-118">Isso garante que várias solicitações não introduzam colisões em tentativas.</span><span class="sxs-lookup"><span data-stu-id="99f9b-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="99f9b-119">Exemplo: detectando exceções transitórias</span><span class="sxs-lookup"><span data-stu-id="99f9b-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="99f9b-120">Aqui está um exemplo usando a retirada exponencial por meio do bloco de aplicativo de tratamento de falhas transitório.</span><span class="sxs-lookup"><span data-stu-id="99f9b-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="99f9b-121">Você pode executar retrocesso e novas tentativas usando a [manipulação de falhas transitória](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="99f9b-121">You can perform backoff and retries using [Transient Fault Handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="99f9b-122">Para obter diretrizes sobre como obter e instalar o pacote NuGet, confira [adicionando o bloqueio de aplicativo de tratamento de falhas transitório à sua solução](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span><span class="sxs-lookup"><span data-stu-id="99f9b-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span></span> <span data-ttu-id="99f9b-123">*Confira também* o [tratamento transitório de falhas](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="99f9b-123">*See also* [Transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

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

## <a name="example-backoff"></a><span data-ttu-id="99f9b-124">Exemplo: retrocesso</span><span class="sxs-lookup"><span data-stu-id="99f9b-124">Example: backoff</span></span>

<span data-ttu-id="99f9b-125">Além de detectar limites de taxa, você também pode executar uma retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="99f9b-125">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

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

<span data-ttu-id="99f9b-126">Você também pode executar uma `System.Action` execução de método com a política de repetição descrita acima.</span><span class="sxs-lookup"><span data-stu-id="99f9b-126">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="99f9b-127">A biblioteca de referência também permite que você especifique um intervalo fixo ou um mecanismo de retrocesso linear.</span><span class="sxs-lookup"><span data-stu-id="99f9b-127">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="99f9b-128">Recomendamos armazenar o valor e a estratégia em um arquivo de configuração para ajustar e ajustar os valores no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="99f9b-128">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="99f9b-129">Para obter mais informações, confira este guia útil em vários padrões de repetição: [padrão de repetição](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="99f9b-129">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="99f9b-130">Por bot por limite de thread</span><span class="sxs-lookup"><span data-stu-id="99f9b-130">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="99f9b-131">A divisão de mensagens no nível de serviço resultará em um maior número de solicitações esperadas por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="99f9b-131">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="99f9b-132">Se você estiver preocupado com a abordagem dos limites, você deve implementar a estratégia de retrocesso descrita acima.</span><span class="sxs-lookup"><span data-stu-id="99f9b-132">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="99f9b-133">Os valores fornecidos abaixo são apenas para previsão.</span><span class="sxs-lookup"><span data-stu-id="99f9b-133">The values provided below are for estimation only.</span></span>

<span data-ttu-id="99f9b-134">Esse limite controla o tráfego que um bot tem permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="99f9b-134">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="99f9b-135">Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="99f9b-135">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="99f9b-136">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="99f9b-136">**Scenario**</span></span> | <span data-ttu-id="99f9b-137">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="99f9b-137">**Time-period (sec)**</span></span> | <span data-ttu-id="99f9b-138">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="99f9b-138">**Max allowed operations**</span></span> |
| --- | --- | --- |
|| <span data-ttu-id="99f9b-139">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-139">1</span></span> | <span data-ttu-id="99f9b-140">178</span><span class="sxs-lookup"><span data-stu-id="99f9b-140">7</span></span> |
| <span data-ttu-id="99f9b-141">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-141">Send to Conversation</span></span> | <span data-ttu-id="99f9b-142">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-142">2</span></span> | <span data-ttu-id="99f9b-143">8</span><span class="sxs-lookup"><span data-stu-id="99f9b-143">8</span></span> |
| <span data-ttu-id="99f9b-144">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-144">Send to Conversation</span></span> | <span data-ttu-id="99f9b-145">até</span><span class="sxs-lookup"><span data-stu-id="99f9b-145">30</span></span> | <span data-ttu-id="99f9b-146">60</span><span class="sxs-lookup"><span data-stu-id="99f9b-146">60</span></span> |
| <span data-ttu-id="99f9b-147">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-147">Send to Conversation</span></span> | <span data-ttu-id="99f9b-148">3600</span><span class="sxs-lookup"><span data-stu-id="99f9b-148">3600</span></span> | <span data-ttu-id="99f9b-149">1800</span><span class="sxs-lookup"><span data-stu-id="99f9b-149">1800</span></span> |
| <span data-ttu-id="99f9b-150">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-150">Create Conversation</span></span> | <span data-ttu-id="99f9b-151">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-151">1</span></span> | <span data-ttu-id="99f9b-152">178</span><span class="sxs-lookup"><span data-stu-id="99f9b-152">7</span></span> |
| <span data-ttu-id="99f9b-153">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-153">Create Conversation</span></span> | <span data-ttu-id="99f9b-154">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-154">2</span></span> | <span data-ttu-id="99f9b-155">8</span><span class="sxs-lookup"><span data-stu-id="99f9b-155">8</span></span> |
| <span data-ttu-id="99f9b-156">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-156">Create Conversation</span></span> | <span data-ttu-id="99f9b-157">até</span><span class="sxs-lookup"><span data-stu-id="99f9b-157">30</span></span> | <span data-ttu-id="99f9b-158">60</span><span class="sxs-lookup"><span data-stu-id="99f9b-158">60</span></span> |
| <span data-ttu-id="99f9b-159">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-159">Create Conversation</span></span> | <span data-ttu-id="99f9b-160">3600</span><span class="sxs-lookup"><span data-stu-id="99f9b-160">3600</span></span> | <span data-ttu-id="99f9b-161">1800</span><span class="sxs-lookup"><span data-stu-id="99f9b-161">1800</span></span> |
| <span data-ttu-id="99f9b-162">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-162">Get Conversation Members</span></span>| <span data-ttu-id="99f9b-163">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-163">1</span></span> | <span data-ttu-id="99f9b-164">14 </span><span class="sxs-lookup"><span data-stu-id="99f9b-164">14</span></span> |
| <span data-ttu-id="99f9b-165">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-165">Get Conversation Members</span></span>| <span data-ttu-id="99f9b-166">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-166">2</span></span> | <span data-ttu-id="99f9b-167">16 </span><span class="sxs-lookup"><span data-stu-id="99f9b-167">16</span></span> |
| <span data-ttu-id="99f9b-168">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-168">Get Conversation Members</span></span>| <span data-ttu-id="99f9b-169">até</span><span class="sxs-lookup"><span data-stu-id="99f9b-169">30</span></span> | <span data-ttu-id="99f9b-170">120</span><span class="sxs-lookup"><span data-stu-id="99f9b-170">120</span></span> |
| <span data-ttu-id="99f9b-171">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-171">Get Conversation Members</span></span>| <span data-ttu-id="99f9b-172">3600</span><span class="sxs-lookup"><span data-stu-id="99f9b-172">3600</span></span> | <span data-ttu-id="99f9b-173">3600</span><span class="sxs-lookup"><span data-stu-id="99f9b-173">3600</span></span> |
| <span data-ttu-id="99f9b-174">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="99f9b-174">Get Conversations</span></span> | <span data-ttu-id="99f9b-175">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-175">1</span></span> | <span data-ttu-id="99f9b-176">14 </span><span class="sxs-lookup"><span data-stu-id="99f9b-176">14</span></span> |
| <span data-ttu-id="99f9b-177">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="99f9b-177">Get Conversations</span></span> | <span data-ttu-id="99f9b-178">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-178">2</span></span> | <span data-ttu-id="99f9b-179">16 </span><span class="sxs-lookup"><span data-stu-id="99f9b-179">16</span></span> |
| <span data-ttu-id="99f9b-180">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="99f9b-180">Get Conversations</span></span> | <span data-ttu-id="99f9b-181">até</span><span class="sxs-lookup"><span data-stu-id="99f9b-181">30</span></span> | <span data-ttu-id="99f9b-182">120</span><span class="sxs-lookup"><span data-stu-id="99f9b-182">120</span></span> |
| <span data-ttu-id="99f9b-183">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="99f9b-183">Get Conversations</span></span> | <span data-ttu-id="99f9b-184">3600</span><span class="sxs-lookup"><span data-stu-id="99f9b-184">3600</span></span> | <span data-ttu-id="99f9b-185">3600</span><span class="sxs-lookup"><span data-stu-id="99f9b-185">3600</span></span> |

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="99f9b-186">Limite por thread para todos os bots</span><span class="sxs-lookup"><span data-stu-id="99f9b-186">Per thread limit for all bots</span></span>

<span data-ttu-id="99f9b-187">Esse limite controla o tráfego que todos os bots podem gerar através de uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="99f9b-187">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="99f9b-188">Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="99f9b-188">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="99f9b-189">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="99f9b-189">**Scenario**</span></span> | <span data-ttu-id="99f9b-190">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="99f9b-190">**Time-period (sec)**</span></span> | <span data-ttu-id="99f9b-191">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="99f9b-191">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="99f9b-192">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-192">Send to Conversation</span></span> | <span data-ttu-id="99f9b-193">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-193">1</span></span> | <span data-ttu-id="99f9b-194">14 </span><span class="sxs-lookup"><span data-stu-id="99f9b-194">14</span></span> |
| <span data-ttu-id="99f9b-195">Enviar para conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-195">Send to Conversation</span></span> | <span data-ttu-id="99f9b-196">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-196">2</span></span> | <span data-ttu-id="99f9b-197">16 </span><span class="sxs-lookup"><span data-stu-id="99f9b-197">16</span></span> |
| <span data-ttu-id="99f9b-198">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-198">Create Conversation</span></span> | <span data-ttu-id="99f9b-199">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-199">1</span></span> | <span data-ttu-id="99f9b-200">14 </span><span class="sxs-lookup"><span data-stu-id="99f9b-200">14</span></span> |
| <span data-ttu-id="99f9b-201">Criar conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-201">Create Conversation</span></span> | <span data-ttu-id="99f9b-202">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-202">2</span></span> | <span data-ttu-id="99f9b-203">16 </span><span class="sxs-lookup"><span data-stu-id="99f9b-203">16</span></span> |
| <span data-ttu-id="99f9b-204">Createconversation</span><span class="sxs-lookup"><span data-stu-id="99f9b-204">CreateConversation</span></span>| <span data-ttu-id="99f9b-205">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-205">1</span></span> | <span data-ttu-id="99f9b-206">14 </span><span class="sxs-lookup"><span data-stu-id="99f9b-206">14</span></span> |
| <span data-ttu-id="99f9b-207">Createconversation</span><span class="sxs-lookup"><span data-stu-id="99f9b-207">CreateConversation</span></span>| <span data-ttu-id="99f9b-208">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-208">2</span></span> | <span data-ttu-id="99f9b-209">16 </span><span class="sxs-lookup"><span data-stu-id="99f9b-209">16</span></span> |
| <span data-ttu-id="99f9b-210">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-210">Get Conversation Members</span></span>| <span data-ttu-id="99f9b-211">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-211">1</span></span> | <span data-ttu-id="99f9b-212">28</span><span class="sxs-lookup"><span data-stu-id="99f9b-212">28</span></span> |
| <span data-ttu-id="99f9b-213">Obter membros de conversa</span><span class="sxs-lookup"><span data-stu-id="99f9b-213">Get Conversation Members</span></span>| <span data-ttu-id="99f9b-214">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-214">2</span></span> | <span data-ttu-id="99f9b-215">32</span><span class="sxs-lookup"><span data-stu-id="99f9b-215">32</span></span> |
| <span data-ttu-id="99f9b-216">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="99f9b-216">Get Conversations</span></span> | <span data-ttu-id="99f9b-217">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-217">1</span></span> | <span data-ttu-id="99f9b-218">28</span><span class="sxs-lookup"><span data-stu-id="99f9b-218">28</span></span> |
| <span data-ttu-id="99f9b-219">Obter conversas</span><span class="sxs-lookup"><span data-stu-id="99f9b-219">Get Conversations</span></span> | <span data-ttu-id="99f9b-220">duas</span><span class="sxs-lookup"><span data-stu-id="99f9b-220">2</span></span> | <span data-ttu-id="99f9b-221">32</span><span class="sxs-lookup"><span data-stu-id="99f9b-221">32</span></span> |

## <a name="bot-per-data-center-limit"></a><span data-ttu-id="99f9b-222">Bot por limite de data center</span><span class="sxs-lookup"><span data-stu-id="99f9b-222">Bot per data center limit</span></span>

<span data-ttu-id="99f9b-223">Esse limite controla o tráfego que um bot tem permissão para gerar em todos os threads em um Data Center (entre vários locatários).</span><span class="sxs-lookup"><span data-stu-id="99f9b-223">This limit controls the traffic that a bot is allowed to generate across all threads in a data center (across multiple tenants).</span></span>

|<span data-ttu-id="99f9b-224">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="99f9b-224">**Time-period (sec)**</span></span> | <span data-ttu-id="99f9b-225">**Máximo de operações permitidas**</span><span class="sxs-lookup"><span data-stu-id="99f9b-225">**Max allowed operations**</span></span> |
| --- | --- |
| <span data-ttu-id="99f9b-226">1</span><span class="sxs-lookup"><span data-stu-id="99f9b-226">1</span></span> | <span data-ttu-id="99f9b-227">508</span><span class="sxs-lookup"><span data-stu-id="99f9b-227">20</span></span> |
| <span data-ttu-id="99f9b-228">1800</span><span class="sxs-lookup"><span data-stu-id="99f9b-228">1800</span></span> | <span data-ttu-id="99f9b-229">8000</span><span class="sxs-lookup"><span data-stu-id="99f9b-229">8000</span></span> |
| <span data-ttu-id="99f9b-230">3600</span><span class="sxs-lookup"><span data-stu-id="99f9b-230">3600</span></span> | <span data-ttu-id="99f9b-231">15000</span><span class="sxs-lookup"><span data-stu-id="99f9b-231">15000</span></span> |
