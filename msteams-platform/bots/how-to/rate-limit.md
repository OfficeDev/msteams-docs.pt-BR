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
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a>Otimize seu bot: limitação de taxa e práticas recomendadas no Microsoft Teams

Como princípio geral, seu aplicativo deve limitar o número de mensagens postadas para uma conversa de canal ou chat individual. Isso garante uma experiência ideal que não considera "spam" para seus usuários finais.

Para proteger o Microsoft Teams e seus usuários, as solicitações de APIs de bot limitam as solicitações de entrada. Os aplicativos que ultrapassarem esse limite receberão um status de `HTTP 429 Too Many Requests` erro. Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo envio de mensagens, enumerações de canal e buscas de lista.

Como os valores exatos dos limites de taxa estão sujeitos a alterações, recomendamos que seu aplicativo implemente o comportamento de retrocesso `HTTP 429 Too Many Requests`apropriado quando a API retornar.

## <a name="handling-rate-limits"></a>Limites de taxa de manipulação

Ao emitir uma operação de SDK do bot Builder, você pode `Microsoft.Rest.HttpOperationException` lidar e verificar o código de status.

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

Em geral, você deve tomar precauções simples para evitar o `HTTP 429` recebimento de respostas. Por exemplo, evite emitir várias solicitações à mesma conversa pessoal ou de canal. Em vez disso, considere o envio em lote das solicitações de API.

Usar uma retirada exponencial com uma tremulação aleatória é a maneira recomendada de lidar com 429s. Isso garante que várias solicitações não introduzam colisões em tentativas.

## <a name="example-detecting-transient-exceptions"></a>Exemplo: detectando exceções transitórias

Aqui está um exemplo usando a retirada exponencial por meio do bloco de aplicativo de tratamento de falhas transitório.

Você pode executar retrocesso e novas tentativas usando [bibliotecas transitórias de tratamento de falhas](/previous-versions/msp-n-p/hh680901(v=pandp.50)). Para obter diretrizes sobre como obter e instalar o pacote NuGet, confira [adicionando o bloqueio de aplicativo de tratamento de falhas transitório à sua solução](/previous-versions/msp-n-p/hh680891(v=pandp.50))

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

## <a name="example-backoff"></a>Exemplo: retrocesso

Além de detectar limites de taxa, você também pode executar uma retirada exponencial.

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

Você também pode executar uma `System.Action` execução de método com a política de repetição descrita acima. A biblioteca de referência também permite que você especifique um intervalo fixo ou um mecanismo de retrocesso linear.

Recomendamos armazenar o valor e a estratégia em um arquivo de configuração para ajustar e ajustar os valores no tempo de execução.

Para obter mais informações, confira este guia útil em vários padrões de repetição: [padrão de repetição](/azure/architecture/patterns/retry).

## <a name="per-bot-per-thread-limit"></a>Por bot por limite de thread

>[!NOTE]
>A divisão de mensagens no nível de serviço resultará em um maior número de solicitações esperadas por segundo (RPS). Se você estiver preocupado com a abordagem dos limites, você deve implementar a estratégia de retrocesso descrita acima. Os valores fornecidos abaixo são apenas para previsão.

Esse limite controla o tráfego que um bot tem permissão para gerar em uma única conversa. Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.

| **Cenário** | **Período de tempo (seg)** | **Máximo de operações permitidas** |
| --- | --- | --- |
| NewMessage | 1  | 7  |
| NewMessage | 2  | 8  |
| NewMessage | até | 60 |
| NewMessage | 3600 | 1800 |
| UpdateMessage | 1  | 7  |
| UpdateMessage | 2  | 8  |
| UpdateMessage | até | 60 |
| UpdateMessage | 3600 | 1800 |
| NewThread | 1  | 7  |
| NewThread | 2  | 8  |
| NewThread | até | 60 |
| NewThread | 3600 | 1800 |
| GetThreadMembers | 1  | 14  |
| GetThreadMembers | 2  | 16  |
| GetThreadMembers | até | 120 |
| GetThreadMembers | 3600 | 3600 |
| GetThread | 1  | 14  |
| GetThread | 2  | 16  |
| GetThread | até | 120 |
| GetThread | 3600 | 3600 |

## <a name="per-thread-limit-for-all-bots"></a>Limite por thread para todos os bots

Esse limite controla o tráfego que todos os bots podem gerar através de uma única conversa. Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.

| **Cenário** | **Período de tempo (seg)** | **Máximo de operações permitidas** |
| --- | --- | --- |
| NewMessage | 1  | 14  |
| NewMessage | 2  | 16  |
| UpdateMessage | 1  | 14  |
| UpdateMessage | 2  | 16  |
| NewThread | 1  | 14  |
| NewThread | 2  | 16  |
| GetThreadMembers | 1  | 28 |
| GetThreadMembers | 2  | 32 |
| GetThread | 1  | 28 |
| GetThread | 2  | 32 |

## <a name="bot-per-data-center-limit"></a>Bot por limite de data center

Esse limite controla o tráfego que um bot tem permissão para gerar em todos os threads em um Data Center (entre vários locatários).

|**Período de tempo (seg)** | **Máximo de operações permitidas** |
| --- | --- |
| 1  | 508 |
| 1800 | 8000 |
| 3600 | 15000 |
