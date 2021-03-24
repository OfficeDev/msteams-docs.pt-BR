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
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a>Otimizar seu bot: limitação de taxa e práticas recomendadas no Microsoft Teams

Como um princípio geral, seu aplicativo deve limitar o número de mensagens que ele posta em um chat individual ou conversa de canal. Isso garante uma experiência ideal que não parece "spammy" para os usuários finais.

Para proteger o Microsoft Teams e seus usuários, as APIs de bot limitam as solicitações de entrada. Os aplicativos que passar por esse limite recebem um `HTTP 429 Too Many Requests` status de erro. Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo o envio de mensagens, enumerações de canal e buscas de lista.

Como os valores exatos dos limites de taxa estão sujeitos a alterações, recomendamos que seu aplicativo implemente o comportamento de backoff apropriado quando a API retornar `HTTP 429 Too Many Requests` .

## <a name="handling-rate-limits"></a>Limites de taxa de manipulação

Ao emissão de uma operação SDK do Construtor de Bots, você pode manipular e `Microsoft.Rest.HttpOperationException` verificar o código de status.

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

## <a name="best-practices"></a>Práticas recomendadas

Em geral, você deve tomar precauções simples para evitar receber `HTTP 429` respostas. Por exemplo, evite a emissão de várias solicitações para a mesma conversa pessoal ou canal. Em vez disso, considere o lote das solicitações de API.

Usar um backoff exponencial com um tremeamento aleatório é a maneira recomendada de lidar com 429s. Isso garante que várias solicitações não introduzam colisões em recuperações.

## <a name="example-detecting-transient-exceptions"></a>Exemplo: detectando exceções transitórias

Aqui está um exemplo usando o backoff exponencial por meio do Bloco de Aplicativos de Tratamento transitório de Falhas.

Você pode executar o backoff e as recuperações usando [o Tratamento transitório de Falhas](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29). Para obter e instalar o pacote NuGet, consulte [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)). *Consulte também Tratamento* [transitório de falhas](/azure/architecture/best-practices/transient-faults).

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

## <a name="example-backoff"></a>Exemplo: backoff

Além de detectar limites de taxa, você também pode executar um backoff exponencial.

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

Você também pode executar uma execução `System.Action` de método com a política de nova tentativa descrita acima. A biblioteca referenciada também permite especificar um intervalo fixo ou um mecanismo de backoff linear.

Recomendamos armazenar o valor e a estratégia em um arquivo de configuração para ajustar e ajustar valores em tempo de execução.

Para obter mais informações, confira este guia prático sobre vários padrões de tentativa: [Padrão de repetir](/azure/architecture/patterns/retry).

## <a name="per-bot-per-thread-limit"></a>Por bot por limite de thread

>[!NOTE]
>A divisão de mensagens no nível de serviço resultará em solicitações mais altas do que as esperadas por segundo (RPS). Se estiver preocupado com a abordagem dos limites, implemente a estratégia de backoff descrita acima. Os valores fornecidos abaixo são apenas para estimativa.

Esse limite controla o tráfego que um bot tem permissão para gerar em uma única conversa. Uma conversa aqui é 1:1 entre bot e usuário, um chat de grupo ou um canal em uma equipe.

| **Cenário** | **Período de tempo (s)** | **Operações máximas permitidas** |
| --- | --- | --- |
| Enviar para Conversa | 1 | 7  |
| Enviar para Conversa | 2 | 8  |
| Enviar para Conversa | 30 | 60 |
| Enviar para Conversa | 3600 | 1800 |
| Criar Conversa | 1 | 7  |
| Criar Conversa | 2 | 8  |
| Criar Conversa | 30 | 60 |
| Criar Conversa | 3600 | 1800 |
| Obter membros da conversa| 1 | 14  |
| Obter membros da conversa| 2 | 16  |
| Obter membros da conversa| 30 | 120 |
| Obter membros da conversa| 3600 | 3600 |
| Obter Conversas | 1 | 14  |
| Obter Conversas | 2 | 16  |
| Obter Conversas | 30 | 120 |
| Obter Conversas | 3600 | 3600 |

>[!NOTE]
> Versões anteriores `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` APIs estão sendo preterida. Elas serão aceleradas para 5 solicitações por minuto e retornarão um máximo de 10 mil membros por equipe. Para atualizar o SDK da Estrutura de Bots e o código para usar os pontos de extremidade mais recentes da API paginada, consulte Alterações na API bot para membros de equipe [e chat.](../../resources/team-chat-member-api-changes.md)

## <a name="per-thread-limit-for-all-bots"></a>Por limite de thread para todos os bots

Esse limite controla o tráfego que todos os bots têm permissão para gerar em uma única conversa. Uma conversa aqui é 1:1 entre bot e usuário, um chat de grupo ou um canal em uma equipe.

| **Cenário** | **Período de tempo (s)** | **Operações máximas permitidas** |
| --- | --- | --- |
| Enviar para Conversa | 1 | 14  |
| Enviar para Conversa | 2 | 16  |
| Criar Conversa | 1 | 14  |
| Criar Conversa | 2 | 16  |
| CreateConversation| 1 | 14  |
| CreateConversation| 2 | 16  |
| Obter membros da conversa| 1 | 28 |
| Obter membros da conversa| 2 | 32 |
| Obter Conversas | 1 | 28 |
| Obter Conversas | 2 | 32 |
