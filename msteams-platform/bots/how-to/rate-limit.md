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
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a>Otimize seu bot: limitação de taxa e práticas recomendadas no Microsoft Teams

Como princípio geral, seu aplicativo deve limitar o número de mensagens postadas para uma conversa de canal ou chat individual. Isso garante uma experiência ideal que não considera "spam" para seus usuários finais.

Para proteger o Microsoft Teams e seus usuários, as solicitações de APIs de bot limitam as solicitações de entrada. Os aplicativos que ultrapassarem esse limite receberão um `HTTP 429 Too Many Requests` status de erro. Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo envio de mensagens, enumerações de canal e buscas de lista.

Como os valores exatos dos limites de taxa estão sujeitos a alterações, recomendamos que seu aplicativo implemente o comportamento de retrocesso apropriado quando a API retornar `HTTP 429 Too Many Requests` .

## <a name="handling-rate-limits"></a>Limites de taxa de manipulação

Ao emitir uma operação de SDK do bot Builder, você pode lidar `Microsoft.Rest.HttpOperationException` e verificar o código de status.

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

Em geral, você deve tomar precauções simples para evitar o recebimento de `HTTP 429` respostas. Por exemplo, evite emitir várias solicitações à mesma conversa pessoal ou de canal. Em vez disso, considere o envio em lote das solicitações de API.

Usar uma retirada exponencial com uma tremulação aleatória é a maneira recomendada de lidar com 429s. Isso garante que várias solicitações não introduzam colisões em tentativas.

## <a name="example-detecting-transient-exceptions"></a>Exemplo: detectando exceções transitórias

Aqui está um exemplo usando a retirada exponencial por meio do bloco de aplicativo de tratamento de falhas transitório.

Você pode executar retrocesso e novas tentativas usando a [manipulação de falhas transitória](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29). Para obter diretrizes sobre como obter e instalar o pacote NuGet, confira [adicionando o bloqueio de aplicativo de tratamento de falhas transitório à sua solução](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN). *Confira também* o [tratamento transitório de falhas](/azure/architecture/best-practices/transient-faults).

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
var retryPolicy = new RetryPolicy(new BotSdkTransientExceptionDetectionStrategy(), exponentialBackoffRetryStrategy);

//Execute any bot sdk action
await retryPolicy.ExecuteAsync(() => connector.Conversations.ReplyToActivityAsync( (Activity)reply) ).ConfigureAwait(false);
```

Você também pode executar uma `System.Action` execução de método com a política de repetição descrita acima. A biblioteca de referência também permite que você especifique um intervalo fixo ou um mecanismo de retrocesso linear.

Recomendamos armazenar o valor e a estratégia em um arquivo de configuração para ajustar e ajustar os valores no tempo de execução.

Para obter mais informações, confira este guia útil em vários padrões de repetição: [padrão de repetição](/azure/architecture/patterns/retry).

## <a name="per-bot-per-thread-limit"></a>Por bot por limite de thread

>[!NOTE]
>A divisão de mensagens no nível de serviço resultará em um maior número de solicitações esperadas por segundo (RPS). Se você estiver preocupado com a abordagem dos limites, você deve implementar a estratégia de retrocesso descrita acima. Os valores fornecidos abaixo são apenas para previsão.

Esse limite controla o tráfego que um bot tem permissão para gerar em uma única conversa. Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.

| **Cenário** | **Período de tempo (s)** | **Máximo de operações permitidas** |
| --- | --- | --- |
| Enviar para conversa | 1  | 7  |
| Enviar para conversa | 2  | 8  |
| Enviar para conversa | até | 60 |
| Enviar para conversa | 3600 | 1800 |
| Criar conversa | 1  | 7  |
| Criar conversa | 2  | 8  |
| Criar conversa | até | 60 |
| Criar conversa | 3600 | 1800 |
| Obter membros de conversa| 1  | 14  |
| Obter membros de conversa| 2  | 16  |
| Obter membros de conversa| até | 120 |
| Obter membros de conversa| 3600 | 3600 |
| Obter conversas | 1  | 14  |
| Obter conversas | 2  | 16  |
| Obter conversas | até | 120 |
| Obter conversas | 3600 | 3600 |

## <a name="per-thread-limit-for-all-bots"></a>Limite por thread para todos os bots

Esse limite controla o tráfego que todos os bots podem gerar através de uma única conversa. Uma conversa aqui é 1:1 entre o bot e o usuário, um chat de grupo ou um canal em uma equipe.

| **Cenário** | **Período de tempo (s)** | **Máximo de operações permitidas** |
| --- | --- | --- |
| Enviar para conversa | 1  | 14  |
| Enviar para conversa | 2  | 16  |
| Criar conversa | 1  | 14  |
| Criar conversa | 2  | 16  |
| Createconversation| 1  | 14  |
| Createconversation| 2  | 16  |
| Obter membros de conversa| 1  | 28 |
| Obter membros de conversa| 2  | 32 |
| Obter conversas | 1  | 28 |
| Obter conversas | 2  | 32 |
