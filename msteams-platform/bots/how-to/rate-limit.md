---
title: Limitação de taxa
description: Limitação de taxas e práticas recomendadas no Microsoft Teams
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 840737178234bcd6e2da1925b0031083717e2b91
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034675"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="8ca6e-104">Otimizar seu bot: limitação de taxa e práticas recomendadas no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8ca6e-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="8ca6e-105">Como um princípio geral, seu aplicativo deve limitar o número de mensagens que ele posta em um chat individual ou conversa de canal.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="8ca6e-106">Isso garante uma experiência ideal que não parece "spammy" para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="8ca6e-107">Para proteger o Microsoft Teams e seus usuários, as APIs de bot limitam as solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="8ca6e-108">Os aplicativos que passar por esse limite recebem um `HTTP 429 Too Many Requests` status de erro.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="8ca6e-109">Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo o envio de mensagens, enumerações de canal e buscas de lista.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="8ca6e-110">Como os valores exatos dos limites de taxa estão sujeitos a alterações, recomendamos que seu aplicativo implemente o comportamento de backoff apropriado quando a API retornar `HTTP 429 Too Many Requests` .</span><span class="sxs-lookup"><span data-stu-id="8ca6e-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="8ca6e-111">Limites de taxa de manipulação</span><span class="sxs-lookup"><span data-stu-id="8ca6e-111">Handling rate limits</span></span>

<span data-ttu-id="8ca6e-112">Ao emissão de uma operação SDK do Construtor de Bots, você pode manipular e `Microsoft.Rest.HttpOperationException` verificar o código de status.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="8ca6e-113">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="8ca6e-113">Best practices</span></span>

<span data-ttu-id="8ca6e-114">Em geral, você deve tomar precauções simples para evitar receber `HTTP 429` respostas.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="8ca6e-115">Por exemplo, evite a emissão de várias solicitações para a mesma conversa pessoal ou canal.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="8ca6e-116">Em vez disso, considere o lote das solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="8ca6e-117">Usar um backoff exponencial com um tremeamento aleatório é a maneira recomendada de lidar com 429s.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="8ca6e-118">Isso garante que várias solicitações não introduzam colisões em recuperações.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="8ca6e-119">Exemplo: detectando exceções transitórias</span><span class="sxs-lookup"><span data-stu-id="8ca6e-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="8ca6e-120">Aqui está um exemplo usando o backoff exponencial por meio do Bloco de Aplicativos de Tratamento transitório de Falhas.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="8ca6e-121">Você pode executar o backoff e as recuperações usando [o Tratamento transitório de Falhas](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="8ca6e-121">You can perform backoff and retries using [Transient Fault Handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="8ca6e-122">Para obter e instalar o pacote NuGet, consulte [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span><span class="sxs-lookup"><span data-stu-id="8ca6e-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span></span> <span data-ttu-id="8ca6e-123">*Consulte também Tratamento* [transitório de falhas](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="8ca6e-123">*See also* [Transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

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

## <a name="example-backoff"></a><span data-ttu-id="8ca6e-124">Exemplo: backoff</span><span class="sxs-lookup"><span data-stu-id="8ca6e-124">Example: backoff</span></span>

<span data-ttu-id="8ca6e-125">Além de detectar limites de taxa, você também pode executar um backoff exponencial.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-125">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

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

<span data-ttu-id="8ca6e-126">Você também pode executar uma execução `System.Action` de método com a política de nova tentativa descrita acima.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-126">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="8ca6e-127">A biblioteca referenciada também permite especificar um intervalo fixo ou um mecanismo de backoff linear.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-127">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="8ca6e-128">Recomendamos armazenar o valor e a estratégia em um arquivo de configuração para ajustar e ajustar valores em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-128">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="8ca6e-129">Para obter mais informações, confira este guia prático sobre vários padrões de tentativa: [Padrão de repetir](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="8ca6e-129">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="8ca6e-130">Por bot por limite de thread</span><span class="sxs-lookup"><span data-stu-id="8ca6e-130">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="8ca6e-131">A divisão de mensagens no nível de serviço resultará em solicitações mais altas do que as esperadas por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="8ca6e-131">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="8ca6e-132">Se estiver preocupado com a abordagem dos limites, implemente a estratégia de backoff descrita acima.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-132">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="8ca6e-133">Os valores fornecidos abaixo são apenas para estimativa.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-133">The values provided below are for estimation only.</span></span>

<span data-ttu-id="8ca6e-134">Esse limite controla o tráfego que um bot tem permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-134">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="8ca6e-135">Uma conversa aqui é 1:1 entre bot e usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-135">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="8ca6e-136">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="8ca6e-136">**Scenario**</span></span> | <span data-ttu-id="8ca6e-137">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="8ca6e-137">**Time-period (sec)**</span></span> | <span data-ttu-id="8ca6e-138">**Operações máximas permitidas**</span><span class="sxs-lookup"><span data-stu-id="8ca6e-138">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8ca6e-139">Enviar para Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-139">Send to Conversation</span></span> | <span data-ttu-id="8ca6e-140">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-140">1</span></span> | <span data-ttu-id="8ca6e-141">7 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-141">7</span></span> |
| <span data-ttu-id="8ca6e-142">Enviar para Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-142">Send to Conversation</span></span> | <span data-ttu-id="8ca6e-143">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-143">2</span></span> | <span data-ttu-id="8ca6e-144">8 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-144">8</span></span> |
| <span data-ttu-id="8ca6e-145">Enviar para Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-145">Send to Conversation</span></span> | <span data-ttu-id="8ca6e-146">30</span><span class="sxs-lookup"><span data-stu-id="8ca6e-146">30</span></span> | <span data-ttu-id="8ca6e-147">60</span><span class="sxs-lookup"><span data-stu-id="8ca6e-147">60</span></span> |
| <span data-ttu-id="8ca6e-148">Enviar para Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-148">Send to Conversation</span></span> | <span data-ttu-id="8ca6e-149">3600</span><span class="sxs-lookup"><span data-stu-id="8ca6e-149">3600</span></span> | <span data-ttu-id="8ca6e-150">1800</span><span class="sxs-lookup"><span data-stu-id="8ca6e-150">1800</span></span> |
| <span data-ttu-id="8ca6e-151">Criar Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-151">Create Conversation</span></span> | <span data-ttu-id="8ca6e-152">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-152">1</span></span> | <span data-ttu-id="8ca6e-153">7 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-153">7</span></span> |
| <span data-ttu-id="8ca6e-154">Criar Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-154">Create Conversation</span></span> | <span data-ttu-id="8ca6e-155">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-155">2</span></span> | <span data-ttu-id="8ca6e-156">8 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-156">8</span></span> |
| <span data-ttu-id="8ca6e-157">Criar Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-157">Create Conversation</span></span> | <span data-ttu-id="8ca6e-158">30</span><span class="sxs-lookup"><span data-stu-id="8ca6e-158">30</span></span> | <span data-ttu-id="8ca6e-159">60</span><span class="sxs-lookup"><span data-stu-id="8ca6e-159">60</span></span> |
| <span data-ttu-id="8ca6e-160">Criar Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-160">Create Conversation</span></span> | <span data-ttu-id="8ca6e-161">3600</span><span class="sxs-lookup"><span data-stu-id="8ca6e-161">3600</span></span> | <span data-ttu-id="8ca6e-162">1800</span><span class="sxs-lookup"><span data-stu-id="8ca6e-162">1800</span></span> |
| <span data-ttu-id="8ca6e-163">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-163">Get Conversation Members</span></span>| <span data-ttu-id="8ca6e-164">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-164">1</span></span> | <span data-ttu-id="8ca6e-165">14 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-165">14</span></span> |
| <span data-ttu-id="8ca6e-166">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-166">Get Conversation Members</span></span>| <span data-ttu-id="8ca6e-167">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-167">2</span></span> | <span data-ttu-id="8ca6e-168">16 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-168">16</span></span> |
| <span data-ttu-id="8ca6e-169">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-169">Get Conversation Members</span></span>| <span data-ttu-id="8ca6e-170">30</span><span class="sxs-lookup"><span data-stu-id="8ca6e-170">30</span></span> | <span data-ttu-id="8ca6e-171">120</span><span class="sxs-lookup"><span data-stu-id="8ca6e-171">120</span></span> |
| <span data-ttu-id="8ca6e-172">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-172">Get Conversation Members</span></span>| <span data-ttu-id="8ca6e-173">3600</span><span class="sxs-lookup"><span data-stu-id="8ca6e-173">3600</span></span> | <span data-ttu-id="8ca6e-174">3600</span><span class="sxs-lookup"><span data-stu-id="8ca6e-174">3600</span></span> |
| <span data-ttu-id="8ca6e-175">Obter Conversas</span><span class="sxs-lookup"><span data-stu-id="8ca6e-175">Get Conversations</span></span> | <span data-ttu-id="8ca6e-176">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-176">1</span></span> | <span data-ttu-id="8ca6e-177">14 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-177">14</span></span> |
| <span data-ttu-id="8ca6e-178">Obter Conversas</span><span class="sxs-lookup"><span data-stu-id="8ca6e-178">Get Conversations</span></span> | <span data-ttu-id="8ca6e-179">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-179">2</span></span> | <span data-ttu-id="8ca6e-180">16 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-180">16</span></span> |
| <span data-ttu-id="8ca6e-181">Obter Conversas</span><span class="sxs-lookup"><span data-stu-id="8ca6e-181">Get Conversations</span></span> | <span data-ttu-id="8ca6e-182">30</span><span class="sxs-lookup"><span data-stu-id="8ca6e-182">30</span></span> | <span data-ttu-id="8ca6e-183">120</span><span class="sxs-lookup"><span data-stu-id="8ca6e-183">120</span></span> |
| <span data-ttu-id="8ca6e-184">Obter Conversas</span><span class="sxs-lookup"><span data-stu-id="8ca6e-184">Get Conversations</span></span> | <span data-ttu-id="8ca6e-185">3600</span><span class="sxs-lookup"><span data-stu-id="8ca6e-185">3600</span></span> | <span data-ttu-id="8ca6e-186">3600</span><span class="sxs-lookup"><span data-stu-id="8ca6e-186">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="8ca6e-187">Versões anteriores `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` APIs estão sendo preterida.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-187">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="8ca6e-188">Elas serão aceleradas para 5 solicitações por minuto e retornarão um máximo de 10 mil membros por equipe.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-188">They will be throttled to 5 requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="8ca6e-189">Para atualizar o SDK da Estrutura de Bots e o código para usar os pontos de extremidade mais recentes da API paginada, consulte Alterações na API bot para membros de equipe [e chat.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="8ca6e-189">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="8ca6e-190">Por limite de thread para todos os bots</span><span class="sxs-lookup"><span data-stu-id="8ca6e-190">Per thread limit for all bots</span></span>

<span data-ttu-id="8ca6e-191">Esse limite controla o tráfego que todos os bots têm permissão para gerar em uma única conversa.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-191">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="8ca6e-192">Uma conversa aqui é 1:1 entre bot e usuário, um chat de grupo ou um canal em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="8ca6e-192">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="8ca6e-193">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="8ca6e-193">**Scenario**</span></span> | <span data-ttu-id="8ca6e-194">**Período de tempo (s)**</span><span class="sxs-lookup"><span data-stu-id="8ca6e-194">**Time-period (sec)**</span></span> | <span data-ttu-id="8ca6e-195">**Operações máximas permitidas**</span><span class="sxs-lookup"><span data-stu-id="8ca6e-195">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8ca6e-196">Enviar para Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-196">Send to Conversation</span></span> | <span data-ttu-id="8ca6e-197">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-197">1</span></span> | <span data-ttu-id="8ca6e-198">14 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-198">14</span></span> |
| <span data-ttu-id="8ca6e-199">Enviar para Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-199">Send to Conversation</span></span> | <span data-ttu-id="8ca6e-200">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-200">2</span></span> | <span data-ttu-id="8ca6e-201">16 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-201">16</span></span> |
| <span data-ttu-id="8ca6e-202">Criar Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-202">Create Conversation</span></span> | <span data-ttu-id="8ca6e-203">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-203">1</span></span> | <span data-ttu-id="8ca6e-204">14 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-204">14</span></span> |
| <span data-ttu-id="8ca6e-205">Criar Conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-205">Create Conversation</span></span> | <span data-ttu-id="8ca6e-206">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-206">2</span></span> | <span data-ttu-id="8ca6e-207">16 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-207">16</span></span> |
| <span data-ttu-id="8ca6e-208">CreateConversation</span><span class="sxs-lookup"><span data-stu-id="8ca6e-208">CreateConversation</span></span>| <span data-ttu-id="8ca6e-209">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-209">1</span></span> | <span data-ttu-id="8ca6e-210">14 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-210">14</span></span> |
| <span data-ttu-id="8ca6e-211">CreateConversation</span><span class="sxs-lookup"><span data-stu-id="8ca6e-211">CreateConversation</span></span>| <span data-ttu-id="8ca6e-212">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-212">2</span></span> | <span data-ttu-id="8ca6e-213">16 </span><span class="sxs-lookup"><span data-stu-id="8ca6e-213">16</span></span> |
| <span data-ttu-id="8ca6e-214">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-214">Get Conversation Members</span></span>| <span data-ttu-id="8ca6e-215">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-215">1</span></span> | <span data-ttu-id="8ca6e-216">28</span><span class="sxs-lookup"><span data-stu-id="8ca6e-216">28</span></span> |
| <span data-ttu-id="8ca6e-217">Obter membros da conversa</span><span class="sxs-lookup"><span data-stu-id="8ca6e-217">Get Conversation Members</span></span>| <span data-ttu-id="8ca6e-218">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-218">2</span></span> | <span data-ttu-id="8ca6e-219">32</span><span class="sxs-lookup"><span data-stu-id="8ca6e-219">32</span></span> |
| <span data-ttu-id="8ca6e-220">Obter Conversas</span><span class="sxs-lookup"><span data-stu-id="8ca6e-220">Get Conversations</span></span> | <span data-ttu-id="8ca6e-221">1</span><span class="sxs-lookup"><span data-stu-id="8ca6e-221">1</span></span> | <span data-ttu-id="8ca6e-222">28</span><span class="sxs-lookup"><span data-stu-id="8ca6e-222">28</span></span> |
| <span data-ttu-id="8ca6e-223">Obter Conversas</span><span class="sxs-lookup"><span data-stu-id="8ca6e-223">Get Conversations</span></span> | <span data-ttu-id="8ca6e-224">2</span><span class="sxs-lookup"><span data-stu-id="8ca6e-224">2</span></span> | <span data-ttu-id="8ca6e-225">32</span><span class="sxs-lookup"><span data-stu-id="8ca6e-225">32</span></span> |
